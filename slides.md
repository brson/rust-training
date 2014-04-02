% A Rust Overview
% Brian Anderson
% April 2, 2014

# Agenda

- Elevator pitch

- Feature laundry list

- Example (what's Rust look like?)

- What applications is Rust good/bad for?

- Rust vs. C/C++/Go

- Roadmap

- Q&A

# The Rust elevator pitch

Rust is a systems programming language that runs blazingly fast, prevents all crashes, and eliminates race conditions.

**Design principles**

- *Memory safety* - Rust programs don't segfault. It's impossible to even create pointers that point to invalid memory.

- *Zero-cost abstractions* - Runtime costs are clear, often free (after optimization), and map efficiently to the machine architecture.

- *Practicality* - Rust is designed through an iterative process that involves actually building large-scale, parallel applications.

# Sidestepping the high/low-level spectrum


```
C/C++               Java                Ruby

<-------------------------------------------->
                      |
More control,         |          Less control,
less safety           |            more safety
                      |

                    Rust

                 More control,
                 more safety
```

# Rust feature laundry list

Convenient high-level features

- algebraic data types, pattern matching
- closures
- generics
- type inference
- safe, multi-paradigm concurrency

Precise low-level control

- minimal runtime
- efficient FFI
- no data races
- optional garbage collection
- controlled unsafety and raw pointer math

# Example

<div style="font-size: 80%">
```
fn main() {
    let data = [("brian", "turnip"), ("alex", "tomato")];
    let mut map = HashMap::new();

    for &(a, b) in data.iter() {
        map.insert(a, b);
    }

    let shared_map = Arc::new(map);

    for (&key, _) in shared_map.iter() {
        let shared_map_clone = shared_map.clone();
        spawn(proc() {
            println!("{} is a {}!",
                     key, shared_map_clone.get(&key));
        })
    }
}
```
</div>

# What Rust is good for

Pick Rust when performance, reliability, scalability, and maintainability are among your highest priorities.

- *Multimedia applications* - audio, video, games

- *Embedding* - using Rust to accelerate hot spots in dynamic languages

- *Embedded systems* - places where reliability is paramount, including consumer applications and perhaps e.g. military/aerospace.

# Rust weaknesses

- *Rapid prototyping* - Compilation is slow.

- *Demanding type system* - Takes comparatively more effort to produce code that compiles.

- *Immaturity* - Libraries especially; finding docs and info.

# Rust vs. C/C++

- *Memory safety*

- *Comperable performance*

- *Similar allocation models*

- *No headers*

- *Less powerful generics* (though more comprehensible)

- *Memory safety*

**Literally **anything** you might write in C or C++ would be better written
  in Rust (eventually)**

# Rust vs. Go

- *Generics*

- *Faster* (optimized compilation, more optimizible model)

- *No race conditions*

- *Faster FFI* - Calling between C and Rust imposes no overhead.

- *Minimal or no runtime* - Works at the lowest levels.

- *Higher compilation time, more static verification*

*Go is good at rapid development, is relatively fast, and not very expressive.
  Rust is expressive, highly reliable, and approaches the performance limit, but is slower to write.*

# Roadmap

* 0.10 this week
* 0.11 July
* 1.0 Late this year

Even if 1.0 is out this year, many aspects,
including libraries will still be *immature*.

# Should you use Rust?

# Questions?

- what about networking in Rust?


