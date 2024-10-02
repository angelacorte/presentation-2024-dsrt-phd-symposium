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

Devices self-organize exchanging messages, abstracting from the communication approach thanks to **alignment**

<div>
<small style="text-align: left">
[1] Beal, J., Pianini, D., Viroli, M. "Aggregate Programming for the Internet of Things." 2015.</br>
</small>
</div>

---

# Alignment<small>[2]</small>

<img src="./images/alignment.svg" width="80%"/>

Devices within the system that execute the same part of the program are **aligned** and capable of communication.

<div>
<small style="text-align: left;">
[2] G. Audrito, F. Damiani, M. Viroli, and R. Casadei, “Run-time management of computation domains in field calculus”
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
Resolvable by using *FCPP* <small>[3]</small>: a tool for developing Aggregate Computing programs.

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
[3] G. Audrito, and G. Torta, "FCPP to aggregate them all."
</small>
</div>

---

# Alternatives?

- Create a new language: **external DSL**

or

- **Hide** the **alignment** at runtime

---

# External DSL: _Protelis_

---

# Hiding alignment at runtime: _ScaFi_

---

# Improving the Simulation Performance for Aggregate Programs Through **Compiler Plugins**

---

# Idea: using a _Compiler Plugin_

---

# Current 


<div>
<small style="text-align: left">
[3] D. Pianini, S. Montagna, and M. Viroli, “Chemical-oriented simulation of computational systems with ALCHEMIST,”
</div>
</small>

---

# Benchmark of the simulations

TODO

---

# Concluding

It works, we're working on it 

![qr code to collective repo](images/qr.svg)
<div style="text-align: center;">
<p><i class="fab fa-github mr-3" style="color: #095aa6;"></i> <a href="https://github.com/Collektive/collektive">Collektive</a></p>
</div>

<!-- [Collektive](https://github.com/Collektive/collektive) -->