Onborading
==========

requires
--------------

- note: verilator version >= 3.92

```bash
module load wake/v0.18.0
module load wit/v0.11.1
```

Initializing the workspace
-----------------------------

```bash
wit init workspace -a git@github.com:KingFrige/block-pio-sifive.git::flow-study

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

wake -v 'runSimWith pioDUT Verilator'

wake -v 'runSimWith pioDUT VCS' # add vcs path to env

wake 'runBitstream "vc707" pioVC707DUT'

# creating an onboarding document
wake makeOnboardingDocument pioDUT
```

- duh generator code
- 修改environment-csoc-iponboarding


> python error
- modified `api-languages-sifive/install-python-pipenv` to specify python version
