PyPANDA Use Cases for NDSS Binary Analysis Workshop Paper
===

This repo contains the code described in our NDSS BAR 2021 paper `PyPANDA: Taming the PANDAmonium of Whole System Dynamic Analysis`.

To run the demos, you should clone this repo and build the Docker container:
```
git clone https://github.com/panda-re/bar2021.git
cd bar2021
docker build -t panda_demos .

mkdir out

docker run -v $(pwd)/out:/out --rm -it panda_demos
```

Then you can run each example with:

## Heap Tracker
```cd heaptracker && make -C tree && python heaptracker.py````
Image graphs for total distinct allocations + total bytes allocated will be created. Copy them to your host to view with `cp *.png /out`

## Unpacker
`cd unpacker && python3 makerecording.py && python3 pyunpacker.py bash --granularity 10000`
Then connect ghidra to your container on port 4768 with ghidra_bridge and browse to the webserver at port 8888.

## IR Eval
`cd ir_eval && python3 run.py`
The `run.py` script takes three optional arguments: `[architecture] [user/kernel space] [target_process]`


Repo status
===
Over the next month we will continue making minor updates to the code in this repository. The NDSS BAR workshop "camera ready" deadline for papers is March 12, 2021 but papers are available today for the BAR workshop. It is with this in mind that we release the code in this repository. The code here works, but we plan to continue cleaning and polishing it in response to reviewer feedback. A final version will be releaed next month.

Paper
====
Our paper can be downloaded from the NDSS BAR website [here](https://www.ndss-symposium.org/ndss-program/bar-2021/)
```
L. Craig, A. Fasano, T. Ballo, T. Leek, B. Dolan-Gavitt, and W. Robertson. "PyPANDA: Taming the PANDAmonium of Whole
System Dynamic Analysis." Proceedings of the 4th Workshop on Binary Analysis Research. 2021.
