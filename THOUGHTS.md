### Questions

What code formatter (if any) does this use?

Why is `Validation` commented?

#### HIE bug

1. Go to `Course.ExactlyOne`
2. Start `eglot`.  There should be a hlint error on `data ExactlyOne` (should be a newtype)
3. Click on `data ExactlyOne`.  Emacs "freezes"
4. Check the HIE log.  There is no message printed until you cancel the action (`C-g`)

### Converting to stack


Looking for .cabal or package.yaml files to use to init the project.
Using cabal packages:
- ./
- projects/NetworkServer/haskell/

Selecting the best among 14 snapshots...

Downloaded lts-12.10 build plan.
Didn't see Agda-2.5.4.1@sha256:af95ca97485ac35501c993e75d4c683a1afbe833170abd24fe5643a0d68ffcb0,27527 in your package indices.
Updating and trying again.
Selected mirror https://s3.amazonaws.com/hackage.fpcomplete.com/
Downloading timestamp
Downloading snapshot
Updating index
Updated package index downloaded
Update complete
Populated index cache.
* Partially matches lts-12.10
    Cabal version 2.2.0.1 found
        - network-server requires >=1.24 && <2

Downloaded nightly-2018-09-21 build plan.
* Partially matches nightly-2018-09-21
    Cabal version 2.2.0.1 found
        - network-server requires >=1.24 && <2

Downloaded lts-11.22 build plan.
* Partially matches lts-11.22
    Cabal version 2.0.1.1 found
        - network-server requires >=1.24 && <2

Downloaded lts-10.10 build plan.
* Partially matches lts-10.10
    Cabal version 2.0.1.1 found
        - network-server requires >=1.24 && <2
    tasty version 0.11.3 found
        - course requires >=1

Downloaded lts-9.21 build plan.
* Partially matches lts-9.21
    tasty version 0.11.3 found
        - course requires >=1

Downloaded lts-8.24 build plan.
* Partially matches lts-8.24
    tasty version 0.11.2.3 found
        - course requires >=1

Downloaded lts-7.24 build plan.
* Partially matches lts-7.24
    HUnit version 1.3.1.2 found
        - course requires >=1.5
    QuickCheck version 2.8.2 found
        - course requires >=2.9
    tasty version 0.11.2.1 found
        - course requires >=1

Downloaded lts-6.35 build plan.
* Partially matches lts-6.35
    Cabal version 1.22.8.0 found
        - network-server requires >=1.24 && <2
    HUnit version 1.3.1.2 found
        - course requires >=1.5
    QuickCheck version 2.8.2 found
        - course requires >=2.9
    tasty version 0.11.2.1 found
        - course requires >=1

Downloaded lts-5.18 build plan.
* Partially matches lts-5.18
    Cabal version 1.22.8.0 found
        - network-server requires >=1.24 && <2
    HUnit version 1.3.1.1 found
        - course requires >=1.5
    QuickCheck version 2.8.1 found
        - course requires >=2.9
    tasty version 0.11.0.3 found
        - course requires >=1

Downloaded lts-4.2 build plan.
* Partially matches lts-4.2
    Cabal version 1.22.6.0 found
        - network-server requires >=1.24 && <2
    HUnit version 1.3.1.0 found
        - course requires >=1.5
    QuickCheck version 2.8.1 found
        - course requires >=2.9
    tasty version 0.11.0.2 found
        - course requires >=1

Downloaded lts-3.22 build plan.
* Partially matches lts-3.22
    Cabal version 1.22.6.0 found
        - network-server requires >=1.24 && <2
    HUnit version 1.2.5.2 found
        - course requires >=1.5
    QuickCheck version 2.8.1 found
        - course requires >=2.9
    tasty version 0.10.1.2 found
        - course requires >=1

Downloaded lts-2.22 build plan.
* Rejected lts-2.22
    ghc-7.8.4 cannot be used for these packages:
        - network-server
    base version 4.7.0.2 found
        - network-server requires >=4.8 && <5

Downloaded lts-1.15 build plan.
* Rejected lts-1.15
    ghc-7.8.4 cannot be used for these packages:
        - network-server
    base version 4.7.0.2 found
        - network-server requires >=4.8 && <5

Downloaded lts-0.7 build plan.
* Rejected lts-0.7
    ghc-7.8.3 cannot be used for these packages:
        - network-server
    base version 4.7.0.1 found
        - network-server requires >=4.8 && <5

Selected resolver: lts-12.10
Resolver 'lts-12.10' does not have all the packages to match your requirements.
    Cabal version 2.2.0.1 found
        - network-server requires >=1.24 && <2

This may be resolved by:
    - Using '--solver' to ask cabal-install to generate extra-deps, atop the chosen snapshot.
    - Using '--omit-packages to exclude mismatching package(s).
    - Using '--resolver' to specify a matching snapshot/resolver

And then...

~/haskell/fp-course $ stack init --resolver lts-12.10 --solver
Looking for .cabal or package.yaml files to use to init the project.
Using cabal packages:
- ./
- projects/NetworkServer/haskell/

Selected resolver: lts-12.10
*** Resolver lts-12.10 will need external packages:
    Cabal version 2.2.0.1 found
        - network-server requires >=1.24 && <2

Using resolver: lts-12.10

Warning: Installed version of cabal-install (2.2.0.0) is newer than stack has been tested with.  If you run into difficulties, consider downgrading.

Using compiler: ghc-8.4.3
Asking cabal to calculate a build plan...
Trying with packages from lts-12.10 as hard constraints...
CallStack (from HasCallStack):
  die', called at ./Distribution/Client/Install.hs:238:21 in main:Distribution.Client.Install
cabal: Could not resolve dependencies:
[__0] trying: course-0.1.4 (user goal)
[__1] rejecting: course:!test (constraint from config file, command line flag,
or user target requires opposite flag selection)
[__1] trying: course:*test
[__2] trying: tasty-quickcheck-0.10 (dependency of course *test)
[__3] trying: optparse-applicative-0.14.2.0 (dependency of tasty-quickcheck)
[__4] trying: process-1.6.3.0/installed-1.6... (dependency of
optparse-applicative)
[__5] trying: filepath-1.4.2/installed-1.4... (dependency of process)
[__6] trying: base-4.11.1.0/installed-4.1... (dependency of course)
[__7] next goal: network-server (user goal)
[__7] rejecting: network-server-0.2.0, network-server-0.1.0 (constraint from
user target requires ==0.0.1)
[__7] trying: network-server-0.0.1
[__8] trying: network-server:setup.filepath~>filepath-1.4.2/installed-1.4...
(dependency of network-server)
[__9] trying: network-server:setup.base~>base-4.11.1.0/installed-4.1...
(dependency of network-server)
[_10] next goal: network-server:setup.Cabal (dependency of network-server)
[_10] rejecting: network-server:setup.Cabal-2.2.0.1/installed-2.2...,
network-server:setup.Cabal-2.4.0.1, network-server:setup.Cabal-2.4.0.0,
network-server:setup.Cabal-2.2.0.1, network-server:setup.Cabal-2.2.0.0,
network-server:setup.Cabal-2.0.1.1, network-server:setup.Cabal-2.0.1.0,
network-server:setup.Cabal-2.0.0.2 (conflict: network-server =>
network-server:setup.Cabal>=1.24 && <2)
[_10] trying: network-server:setup.Cabal-1.24.2.0
[_11] next goal: network-server:setup.process (dependency of
network-server:setup.Cabal)
[_11] rejecting:
network-server:setup.process~>process-1.6.3.0/installed-1.6... (conflict:
network-server:setup.Cabal => network-server:setup.process>=1.1.0.1 && <1.5)
[_11] rejecting: network-server:setup.process-1.6.3.0/installed-1.6...
(multiple instances)
[_11] rejecting: network-server:setup.process-1.6.4.0,
network-server:setup.process-1.6.3.0, network-server:setup.process-1.6.2.0,
network-server:setup.process-1.6.1.0, network-server:setup.process-1.6.0.0,
network-server:setup.process-1.5.0.0 (conflict: network-server:setup.Cabal =>
network-server:setup.process>=1.1.0.1 && <1.5)
[_11] rejecting: network-server:setup.process-1.4.3.0 (conflict:
network-server:setup.filepath =>
network-server:setup.base==4.11.1.0/installed-4.1...,
network-server:setup.process => network-server:setup.base>=4.4 && <4.11)
[_11] rejecting: network-server:setup.process-1.4.2.0,
network-server:setup.process-1.4.1.0, network-server:setup.process-1.4.0.0
(conflict: network-server:setup.filepath =>
network-server:setup.base==4.11.1.0/installed-4.1...,
network-server:setup.process => network-server:setup.base>=4.4 && <4.10)
[_11] rejecting: network-server:setup.process-1.3.0.0,
network-server:setup.process-1.2.3.0, network-server:setup.process-1.2.2.0,
network-server:setup.process-1.2.1.0 (conflict: network-server:setup.filepath
=> network-server:setup.base==4.11.1.0/installed-4.1...,
network-server:setup.process => network-server:setup.base>=4.4 && <4.9)
[_11] rejecting: network-server:setup.process-1.2.0.0 (conflict:
network-server:setup.filepath =>
network-server:setup.base==4.11.1.0/installed-4.1...,
network-server:setup.process => network-server:setup.base>=4.4 && <4.8)
[_11] rejecting: network-server:setup.process-1.1.0.2 (conflict:
network-server:setup.filepath =>
network-server:setup.base==4.11.1.0/installed-4.1...,
network-server:setup.process +/-base4 => network-server:setup.base>=3 && <4.7)
[_11] rejecting: network-server:setup.process-1.1.0.1 (conflict:
network-server:setup.filepath==1.4.2/installed-1.4...,
network-server:setup.process => network-server:setup.filepath>=1.1 && <1.4)
[_11] rejecting: network-server:setup.process-1.1.0.0,
network-server:setup.process-1.0.1.5, network-server:setup.process-1.0.1.4,
network-server:setup.process-1.0.1.3, network-server:setup.process-1.0.1.2,
network-server:setup.process-1.0.1.1, network-server:setup.process-1.0.0.0
(conflict: network-server:setup.Cabal => network-server:setup.process>=1.1.0.1
&& <1.5)
After searching the rest of the dependency tree exhaustively, these were the
goals I've had most trouble fulfilling: network-server:setup.Cabal (787),
network-server (665), network-server:setup.process (558),
network-server:setup.filepath (269), network-server:setup.base (222), filepath
(55), process (51), doctest (48), optparse-applicative (38), base (30),
tasty-quickcheck (17), ghc (8), course (4), network-server:test (4),
ghc:buildable (3), course:test (3)

Could not parse cabal-install errors:

>>>> Cabal errors begin
<<<< Cabal errors end

CallStack (from HasCallStack):
  error, called at src/Stack/Solver.hs:130:25 in stack-1.7.1-39g4pqWg5pP94D3gA1kGJe:Stack.Solver


```
After searching the rest of the dependency tree exhaustively, these were the
goals I've had most trouble fulfilling
```

... since when did cabal respond with *I*?

# Running a single test

Via stack:

```
stack test --ta '--pattern "Tests.List."'
```

`show-detail` seems to be to do with cabal showing test output.  Not sure how to port this to stack.

# Doctests

I've installed doctest using `stack install doctest`, but can't get them to work :(
`stack exec doctest` gives me nothing, and of course running it on a single file gives import errors.




(file-name-base (buffer-file-name (get-buffer (current-buffer) ) ) )

# Completion

1. Go to `Optional.hs`
2. Under `bindOptional` type `bindOp`
3. Investigate `company-diag`:

```
Emacs 26.1 (x86_64-pc-linux-gnu) of 2018-07-05 on juergen
Company 0.9.4

company-backends: (company-lsp company-bbdb company-nxml company-css company-eclim company-semantic company-clang company-xcode company-cmake company-capf company-files
         (company-dabbrev-code company-gtags company-etags company-keywords)
         company-oddmuse company-dabbrev)

Used backend: company-capf
Major mode: haskell-mode
Prefix: "bindOp"
Completions: none
```
