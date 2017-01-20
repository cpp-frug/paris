Boson
=====
Un framework pour la concurrence coopérative
--------------------------------------------

[cppfrug.org / paris / events / 2017-01-19_n14 / Boson](http://cpp-frug.github.io/paris/events/2017-01-19_n14/Boson/)

[github.com / cpp-frug / paris / events / 2017-01-19_n14 / Boson](https://github.com/cpp-frug/paris/blob/master/events/2017-01-19_n14/Boson/README.md)


L'existant
----------

&nbsp;

- Fibres dans `folly`
- `boost::fiber`
- `Raftlib`



Inspiré du langage Go
---------------------

&nbsp;

- Fibres au coeur du framework
- Le netpoller : I/O asynchrone automagique
- Channels



Pourquoi ?
----------

&nbsp;

- Pas d'I/O automagique possible avec l'existant
- Dépasser la lourdeur des algos "asynchrone"
- Très bon exercice d'apprentissage



Lancer des fibres
-----------------

```c++
void timer(int out, bool& stopper) {
  while(!stopper) {
    boson::sleep(1000ms);
    boson::write(out,"Tick !\n",7);
  }
  boson::write(out,"Stop !\n",7);
}

void user_input(int in, bool& stopper) {
  char buffer[1];
  boson::read(in, &buffer, sizeof(buffer));
  stopper = true;
}

int main(int argc, char *argv[]) {
  bool stopper = false;
  boson::run(1, [&stopper]() {
    boson::start(timer, 1, stopper);
    boson::start(user_input, 0, stopper);
  });
}
```



Communiquer entre fibres
------------------------

```c++
boson::run(1, []() {
  boson::channel<int, 1> pipe;

  boson::start([](auto input) -> void {
      int i = 0;
      while (input >> i)
        std::cout << "Received " << i << "\n";
  }, pipe);

  boson::start([](auto output) -> void {
      for (int i = 0; i < 5; ++i) {
        output << i;
        std::cout << "Sent " << i << "\n";
      }
      output.close();
  }, pipe);
});
```


> Sent 0 <br/>
> Received 0 <br/>
> Sent 1 <br/>
> Received 1 <br/>
> Sent 2 <br/>
> Received 2 <br/>
> Sent 3 <br/>
> Received 3 <br/>
> Sent 4 <br/>
> Received 4 <br/>



Blocage simultané
-----------------

```c++
struct producer {
template <class Duration, class Channel>
void operator() (Duration wait, Channel pipe, int data) const {
  boson::sleep(wait);
  pipe << data;
}
};

int main(int argc, char *argv[]) {
  boson::run(1, []() {
    boson::channel<int, 1> pipe1, pipe2;

    boson::start(
        [](auto in1, auto in2) -> void {
          int result;
          for (int i = 0; i < 2; ++i)
            select_any(
                event_read(in1, result, [&](bool) { std::cout << "Received " << result << "\n"; }),
                event_read(in2, result, [&](bool) { std::cout << "Received " << result << "\n"; }));
        },
        pipe1, pipe2);

    boson::start(producer{}, 500ms, pipe1, 1);
    boson::start(producer{}, 0ms, pipe2, 2);
  });
}
```


> Received 2 <br/>
> Received 1 <br/>



Blocage simultané hétérogène
----------------------------

```c++
int main(int argc, char *argv[]) {
  boson::run(1, []() {
    boson::channel<int, 1> pipe;

    boson::start(
        [](auto in) -> void {
          int result;
          for (int i = 0; i < 2; ++i)
            select_any(
                event_read(0, &result, sizeof(int),
                           [&](ssize_t) { std::cout << "Received on stdin " << result << "\n"; }),
                event_read(in, result,
                           [&](bool) { std::cout << "Received on chan " << result << "\n"; }),
                event_timer(1000ms,  //
                            [&]() { std::cout << "Timeout\n"; }));
        },
        pipe);

    pipe << 2;
  });
}
```



Retour d'expérience
-------------------
Les algos lock-free
===================


### Le Saint Graal
## Queue *MPMC* wait-free, unbounded, serialisable


### Le Saint Graal
## Queue MPMC *wait-free*, unbounded, serialisable


### Le Saint Graal
## Queue MPMC wait-free, *unbounded*, serialisable


### Le Saint Graal
## Queue MPMC wait-free, unbounded, *serialisable*


## Single Producer, Single Consumer
## Single Producer, Multiple Consumers
## Multiple Producers, Single Consumer
## Multiple Produces, Multiple Consumers


## Lock-free
### versus
## Wait-free


## Bounded
### versus
## Unbounded


### MPMC
## LCRQ (2013)


## LCRQ dans Boson



Broken demo time
================



<https://github.com/duckie/boson>
