This is the software repo for the LHSS (Laurel Heights Secondary School) EVC team.

# public-telemetry setup guide
note: this is for linux, should theoretically work on macos directly and on windows w/ a different serial library + waitress or flask development wsgi server (js use wsl vro)

there are 3 main parts
1. public-telemetry/tel-host
2. public-telemetry/tel-server
3. public-telemetry/tel-interface
- tel-host runs on the computer with the serial radio attached. it receives records from the radio, processes them, and POSTs them to the server. this is the code that logs the csv datafile.
- tel-server is a dumb flask server; it just receives records from the host and gives them out to the web-interface when requested. this can run on a different computer but its easier to have it on the same one.
- tel-interface is the javascript frontend; it GETs data from the server and draws the charts

first, clone the repo w/
```bash
git clone https://github.com/liub1606/evcSoftware.git
```

then, cd into the public-telemetry directory
```bash
cd evcSoftware/public-telemetry
```

make a python virtual environment for the libraries
```bash
mkdir venv
python -m venv venv
. venv/bin/activate
pip install -r requirements.txt
```
