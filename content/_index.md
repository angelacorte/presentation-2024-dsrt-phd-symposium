+++

title = "Improving the Simulation Performance for Aggregate Programs Through Compiler Plugins"
description = "DS-RT 2024 PhD Symposium presentation"
outputs = ["Reveal"]

+++

# Improving the Simulation Performance for <span class="fragment custom red" data-fragment-index="0">Aggregate Programs</span> Through Compiler Plugins

<p class="fragment fade-out" data-fragment-index="0">
<a href="mailto:angela.cortecchia@unibo.it"><b>Angela Cortecchia</b></a></br>
GARR research fellow & (soon) PhD Student @UniBo</br>

<img src="example-background.svg" style="width: 30%"/>
</p>

---

# What is Aggregate Computing<small>[1]</small>?

<img src="./images/acDevices.svg" width=60%>


A macro-programming approach that defines the **collective behavior** of a heterogeneous set of devices in a **self-organizing system**.
<!-- Based on the **Field Calculus**<small>[2]</small>, operates by manipulating distributed data structures called *fields*. -->

Devices self-organize exchanging messages, abstracting from the communication approach thanks to **alignment**.

Based on the **Field Calculus**<small>[2]</small>, operates by manipulating distributed data structures called *fields*.

<div>
<small style="text-align: left">
[1] Beal, J., Pianini, D., Viroli, M. "Aggregate Programming for the Internet of Things." 2015.</br>
[2] Audrito, G., Viroli, M., Damiani, F., Pianini, D., Beal, J. "A Higher-Order Calculus of Computational Fields." 2019.
</small>
</div>

---

# Alignment<small>[3]</small>

<img src="./images/alignment.svg" width="70%"/>

Devices within the system that execute the same part of the program are **aligned** and capable of communication.

<div>
<small style="text-align: left;">
[3] G. Audrito, F. Damiani, M. Viroli, and R. Casadei, “Run-time management of computation domains in field calculus”
</small>
</div>

---

# Improving the **Simulation Performance** for Aggregate Programs Through Compiler Plugins

---

# Simulating _Aggregate Computing_ systems

Simulations are part of the **development cycle**.

**Scalability limitation**: </br>challenges in scaling simulations to hundreds or more devices simultaneously.

Simulations _must_ be reactive also on high scales.

---

# Scalability limitation

{{% multicol %}}

{{% col class="text-start" %}}
Resolvable by using *FCPP* <small>[4]</small>: a tool for developing Aggregate Computing programs.

*FCPP limitations*: 
- **non-friendly** language;
- aggregate **base-mechanism not hidden**.

{{% /col %}}
{{% col %}}

For example

![fcpp](images/fcpp.svg)
<!-- ```cpp
//manual alignment
field<double> f = nbr(CALL, 4.2);
int n = nbr(CALL, 0, [&](field<int> a){
    return min_hood(CALL, a)
});
``` -->
{{% /col %}}

{{% /multicol %}}

<div>
<small style="text-align: left;">
[4] G. Audrito, and G. Torta, "FCPP to aggregate them all."
</small>
</div>

---

# Alternatives?

- Create a new language: **external DSL**

or

- **Hide** the **alignment** at runtime with **internal DSL**

---

# External DSL: _Protelis_ <small>[5]</small>

Java-like external DSL.

Hides pretty well main aggregate computing mechanisms, such as alignment.

*Protelis limitations*:
- being a standalone language, its interpreter and compiler must be **self-maintained**;
- **slower in complex programs**, due to its compiler.

Those limitations can be overcome by leveraging on an **internal DSL**.

<div>
<small style="text-align: left;">
[5] D. Pianini, M. Viroli, and J. Beal, “Protelis: practical aggregate programming”
</small>
</div>

---

# Internal DSL: _ScaFi_ <small>[6]</small>

Scala-based internal DSL.

Alignment **hidden at runtime** doing stack investigation.

*ScaFi limitations*:
- still some limitations at alignment and language-level;
- not very performant, due to alignment management.

<div>
<small style="text-align: left;">
[6] R. Casadei, M. Viroli, G. Aguzzi, and D. Pianini, “Scafi: A scala DSL and toolkit for aggregate programming”
</small>
</div>

---

# Improving the Simulation Performance for Aggregate Programs Through **Compiler Plugins**

<img src="images/SOTAtable.svg"/>

---

# Idea: use a _Compiler Plugin_

Annotates the aggregate program on a stack at compile time.

Devices with the same annotations in the stack are "aligned" and can communicate.

_Pros_:
- Expressivity untouched;
- No overhead of the classic approaches.

---

# Meet **Collektive**

{{% multicol %}}

{{% col %}}
<img src="images/collektive-logo.svg" width="60%">
{{% /col %}}

{{% col class="col-md-8 text-start" %}}
- Internal DSL in Kotlin Multiplatform;
- Alignment made automatically behind the scene through compiler plugin.
- Linked to the general purpose _Alchemist_ <small>[7]</small> simulator, which can execute also _Protelis_ and _ScaFi_ programs.

First implementation of the prototype DSL used to develop experiments related to the morphogenesis of plants.

{{% /col %}}

{{% /multicol %}}

<div>
<small style="text-align: left">
[7] D. Pianini, S. Montagna, and M. Viroli, “Chemical-oriented simulation of computational systems with ALCHEMIST”
</div>
</small>

---

# **Improving** the Simulation **Performance** for Aggregate Programs Through Compiler Plugins

---

{{% multicol %}}

{{% col %}}
## Reference scenario

_Channel with obstacles_ <small>[8]</small>:</br>
an algorithm to build a redundant channel between two points in a meshed network,
avoiding obstacles and adapting to topology changes.

<img src="images/channelWithObstacles.png" width="70%"/>
<!--  -->
{{% /col %}}

{{% col %}}

## Results

- External DSLs (_Protelis_) has performance disadvantages in complex programs, respect to internal DSLs (_Collektive_ & _ScaFi_);
- Compiler plugin optimizes performance between internal DSLs, thanks to the management of the alignment.

<img src="images/channel.svg" width="72%"/>

<!-- <div class="r-stack">
  <img
    class="fragment current-visible fade-out"
    data-fragment-index="0"
    src="images/channelWithObstacles.png"
  />
  <img
    class="fragment"
    data-fragment-index="1"
    src="images/channel.svg"    
  />
</div> -->
{{% /col %}}

{{% /multicol %}}

<div>
<small style="text-align: left">
[8] R. Casadei, G. Fortino, D. Pianini, A. Placuzzi, C. Savaglio, and M. Viroli, “A methodology and simulation-based toolchain for estimating deployment performance of smart collective services at the edge"
</small>
</div>

---

# Conclusion

{{% multicol %}}

{{% col class="col-md-8" %}}
This work demonstrates that the technology used within a tool affects program execution time.

### Future works

- Further enhancing for efficient and faster execution across various platforms;
- Create a standard library of aggregate building blocks;
- Exploit the tool to the concept of "collective operating systems".

{{% /col %}}

{{% col %}}
![qr code to collective repo](images/qr.svg)
<div style="text-align: center;">
<p><i class="fab fa-github mr-3" style="color: #095aa6;"></i> <a href="https://github.com/Collektive/collektive">Collektive</a></p>
</div>
{{% /col %}}

{{% /multicol %}}



<!-- [Collektive](https://github.com/Collektive/collektive) -->