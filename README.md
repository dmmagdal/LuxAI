# Lux AI

Description: My attempts/research into the Lux AI challenge and apply different machine learning techniques to maximize my score.


### Setup (Season 1):

 - Install the node package for the game (`npm install -g @lux-ai/2021-challenge@latest`). Be sure to use nodeJS v12+.
 - Python Kit
     - Set up your Python environment (packages). Use Python 3.7+.
     - Copy the Python starter kit (`Lux-Design-S1/kits/python/simple`) to some path.
     - To run the challenge, enter the following command: `npx lux-ai-2021 AI_1_PATH AI_2_PATH --width WIDTH --height HEIGHT` where `AI_1_PATH` & `AI_2_PATH` are the path's to the respective `main.py` (usually it's `simple/main.py` for you to run your local AI instance).
 - Running the challenge will generate a `replays` directory with a JSON file for that last run
 - You can use the [Lux-Viewer-S1 repo](https://github.com/Lux-AI-Challenge/Lux-Viewer-S1) to watch the replay offline. Online replay engine at https://2021vis.lux-ai.org is currently still available as of 12/29/23.
     - The `dist.zip` & `dist/` items are for release v3.1.0 for the Lux-Viewer-S1 repo (most recent version, uploaded 08/31/21).


### Setup (Season 2):

 - Create a conda environment for the game.
     - `conda create -n "luxai_s2" "python==3.9"` (use Python >=3.7, <3.11)
     - `conda activate luxai_s2`
     - Install the environment (CPU or GPU version):
         - `pip install --upgrade luxai_s2` (CPU)
         - `pip install juxai-s2` (GPU - requires compatible GPU)
 - Verify installation by running the CLI tool, replacing `path/to/bot/main.py` with a path to a bot (e.g. the starter kit in `kits/python/main.py`) and run `luxai-s2 path/to/bot/main.py path/to/bot/main.py -v 2 -o replay.json`


### Notes:

 - This game does support a local "offline" mode for Seasons 1 & 2. There are a few caveats in terms of the environment setup.
     - For Season 1, one must install nodeJS v12+ to globaly install the competition's design (`npm install -g @lux-ai/2021-challenge@latest`). For Python, the environment must be Python 3.7+.
         - If you want to use Jupyter or Kaggle notebooks, the `kaggle-environments` package is required on top of the npm package (see the [Season 1 Kaggle Notebook](https://www.kaggle.com/code/stonet2000/lux-ai-season-1-jupyter-notebook-tutorial/notebook)). Refer to the notes in the [README.md](https://github.com/dmmagdal/HaliteRL/blob/main/README.md) for the [HaliteRL repo](https://github.com/dmmagdal/HaliteRL) I have regarding issues with setting up/installing the `kaggle-environemnts` package.
     - For Season 2, the game is 100% runnable from Python. Refer to the **Getting Started** section of the README.md for the Season 2 repository OR the [Setup (Season 2)](#setup-season-2) section in this README.md for the specifics.
 - Season 1
     - I created a dockerfile to containerize the environment to run the LuxAI program in `Dockerfile-S1`. The following docker commands I found helpful to using the docker image my dockerfile creates (run from the repo root):
         - Build the image: `docker build -t lux-ai-s1 -f Dockerfile-S1 .`
         - Run the docker image in interactive mode (launches bash terminal on startup): `docker run -it --name lux-s1-runner -v $(pwd)/:/run-LuxAI-S1 --rm lux-ai-s1 bash`
             - `-v` mounts a volume
             - `--rm` deletes the container once the container exits
             - `--name` gives the container a name
             - `-d` detaches the container (runs it in the background & returns the container ID)
             - `lux-s1-runner` is the container name while `lux-ai-s1` is the image name (from the build step)
             - `run-LuxAI-S1` is the working directory in the image (see the actual dockerfile)
             - Reference to additional arguments when issuing `docker run` command can be found in the [docker documentation](https://docs.docker.com/engine/reference/commandline/run/)
         - Once inside the active container, use the following command to run the experiment: `lux-ai-2021 path/to/main.py path/to/main.py --out=path/to/replay_file.json`
             - Will usually set `--out` to be `replays/S1/$(date +"%Y_%m_%d-%H_%M_%S").json`
                 - `date +"%Y_%m_%d-%H_%M_%S"` just takes the container `date` and formats that
                 - The container date is used to name the most recent replay JSON file
             - Additional arguments (reference [Lux-Design-S1 README.md](/Lux-Design-S1/README.md)):
                 - `--seed` the seed of the map/match
                 - `--storeLogs` stores agent logs
                 - `--storeReplay` stores match replays
                 - `--statefulReplay` generates stateful replays instead of action-based replays
                 - `--convertToStateful` converts action-based replays into stateful replays
                 - `--loglevel` sets the logging level (default is 2 - prints all game errors & warnings to terminal) - has range 0 to 4
             - By default, the game generates minimum, action-based replays (small in size & work on the vizualizer but lacks state information like resources on the map in each turn).
     - The original `Lux-Design-S1` repo contains its own shell script and dockerfile for running the LuxAI program.
         - This dockerfile is called upon by another script (`cli.sh` found [here](/Lux-Design-S1/cli.sh) in the `Lux-Design-S1` repo).
             - [dockerfile](/Lux-Design-S1/Dockerfile)
             - [cli.sh](/Lux-Design-S1/cli.sh)
         - Refer to the documentation in the [/Lux-Design-S1 README.md](/Lux-Design-S1/README.md) for more on how to use the `clu.sh` script to instantiate the docker image.
         - There are many small differnces between this dockerfile and the dockerfile I wrote above. The main big difference is that my dockerfile reads the `requirementsS1.txt` file to instally any necessary dependencies for the bots.
     - I created a second dockerfile to containerize the environment to run the LuxAI local replay viewer in `Dockerfile-S1-Viewer`. The following docker commands I found helpful to using the docker image my dockerfile creates (run from the repo root):
         - Build the image: `docker build -t lux-ai-s1-viewer -f Dockerfile-S1-Viewer .`
         - Run the docker image in interactive mode (launches bash terminal on startup): `docker run -it --name lux-viewer -p 5001:5000 --rm viewer bash`
             - `--rm` deletes the container once the container exits
             - `--name` gives the container a name
             - `-p` or `--publish` publishes a container's port to the host
             - `lux-viewer` is the container name while `lux-ai-s1-viewer` is the image name (from the build step)
             - Reference to additional arguments when issuing `docker run` command can be found in the [docker documentation](https://docs.docker.com/engine/reference/commandline/run/)
 - Season 2



### References:

 - Lux AI Documentation:
     - [Season 1 Kaggle Competition Page](https://www.kaggle.com/c/lux-ai-2021)
     - [Season 2 Kaggle Competition Page](https://www.kaggle.com/competitions/lux-ai-season-2-neurips-stage-2)
     - [Lux Design S1 Repo](https://github.com/Lux-AI-Challenge/Lux-Design-S1)
     - [Lux Design S2 Repo](https://github.com/Lux-AI-Challenge/Lux-Design-S2)
     - [Season 1 Specs](https://www.lux-ai.org/specs-2021)
     - [Season 2 Specs](https://www.lux-ai.org/specs-s2)
     - [Season 1 Jupyter Notebook Tutorial](https://www.kaggle.com/code/stonet2000/lux-ai-season-1-jupyter-notebook-tutorial/notebook)
 - Sentdex's Tutorials:
     - [Coding Adventure with Kaggle and Lux AI](https://www.youtube.com/watch?v=6_GXTbTL9Uc&ab_channel=sentdex) YouTube video (season 1)