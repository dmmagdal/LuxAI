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


### Setup (Season 2):

 - 


### Notes:

 - This game does support a local "offline" mode for Seasons 1 & 2. There are a few caveats in terms of the environment setup.
     - For Season 1, one must install nodeJS v12+ to globaly install the competition's design (`npm install -g @lux-ai/2021-challenge@latest`). For Python, the environment must be Python 3.7+.
         - If you want to use Jupyter or Kaggle notebooks, the `kaggle-environments` package is required on top of the npm package (see the [Season 1 Kaggle Notebook](https://www.kaggle.com/code/stonet2000/lux-ai-season-1-jupyter-notebook-tutorial/notebook)). Refer to the notes in the [README.md](https://github.com/dmmagdal/HaliteRL/blob/main/README.md) for the [HaliteRL repo](https://github.com/dmmagdal/HaliteRL) I have regarding issues with setting up/installing the `kaggle-environemnts` package.
     - For Season 2, the game is 100% runnable from Python. Refer to the **Getting Started** section of the README.md for the Season 2 repository for the specifics.


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