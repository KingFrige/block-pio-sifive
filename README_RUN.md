Onborading
==========

requires
--------------

- note: verilator version >= 3.92

```bash
module load wake/0.18.0
module load wit/0.11.1
```

Initializing the workspace
-----------------------------

```bash
wit init workspace -a git@github.com:sifive/block-pio-sifive.git
cd workspace

wit add-pkg git@github.com:sifive/environment-example-sifive.git

wit update

wit fetch-scala
```

build block-pio-sifive
------------------
```sh
wake --init .

wake makeRTL pioDUT

wake -v 'runSimWith pioDUT VCS'
wake -v 'runSimWith pioDUT Verilator'

wake 'runBitstream "vc707" pioVC707DUT'

# creating an onboarding document
wake makeOnboardingDocument pioDUT
```

- duh generator code
- 修改environment-csoc-iponboarding


> python error
- modified `api-languages-sifive/install-python-pipenv` to specify python version

duh_training_small_initiator
------------
```sh
wit fetch-scala

wake makeRTL loopbackDUT

# note: verilator version >= 3.92
wake 'runSim loopbackDUT'
# or wake 'runSimWith loopbackDUT VCS'
```

soc-freedom-sifive
-------------------------
### Initializing the workspace
```sh
wit init workspace -a git@github.com:sifive/soc-freedom-sifive.git
cd workspace
wake --init .

wit fetch-scala
```
### Compiling scala
```sh
wake -v compileScalaModule e300ScalaModule
wake -v compileScalaModule u500ScalaModule
```

### Generating verilog
```sh
wake -v makeRTL e300ArtyDUTPlan
wake -v makeRTL u500VC707DUTPlan
```

### run simulation


demo-block
------------
```sh
wake 'runSim pioDUT'
```

delivery demo
-----------------
```
wake -vv 'makeRTL tlgpioDUT'
```

