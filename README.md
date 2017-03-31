# PyGrunt

Pygrunt contains a class that utilizes the request library to interact with [grunt](https://github.com/Mayo-QIN/grunt) dockers.

## Start up an example docker

```
docker fetch mayoqin/grunt
docker run --rm -it -p 9901:9901 mayoqin/grunt
```

Interface with the docker

```
from pygrunt import *

g = grunt("http://localhost:9901")

# list available services
for service in g.services.keys():
    print service

# Try out the "echo service"
j = g.echo
j.Message = "Hi from grunt"

# Submit the job to grunt, and wait for completion
job = j()
job.wait()

print "got output! {}".format ( job.output() )

# Wait for a job
j = g.sleep
j.seconds = 10
job = j()
job.wait()

# Upload and download data
j = g.copy
j.input = 'README.md'
j.output = 'README.copy.md'

job = j()
job.wait()
# writes READEM.copy.md to current directory.
job.save_output ( 'output', directory='.' )
```
