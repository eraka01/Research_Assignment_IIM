# Combinatorial Optimization enriched Machine Learning to solve the Dynamic Vehicle Routing Problem with Time Windows


## Problem Statement

As E-commerce growth has intensified customer demands for faster deliveries, prompting logistics service providers (LSPs) to offer same-day delivery. This has made last-mile delivery increasingly challenging due to the need for quick, efficient order dispatch and vehicle routing.

Traditional day-ahead planning is insufficient for same-day delivery, requiring dynamic, real-time decision-making to handle incoming orders. Current solutions, such as reinforcement learning and stochastic optimization, struggle with high-dimensional combinatorial problems and computational efficiency.

To address this, they have proposed a machine learning (ML) pipeline integrated with a combinatorial optimization (CO) layer. The ML part helps predict future orders and uncertainties, while the CO part quickly finds the best delivery routes, ensuring fast and reliable same-day deliveries.

## Implementing the problem

This repository contains all relevant scripts and data sets to reproduce the results from the paper. 


The structure of this repository is as follows:  
./evaluation: code to evaluate the learned ML-CO policy  
./experiments: directory containing all anticipative lower bound target solutions for different experiments  
./features: code to create features  
./instances: directory containing all static instances  
./pchgs: code to run PC-HGS  
./training: code to train ML-CO policy 


### Part I - Installing PC-HGS

Step 1- Cloning the repository and initializing submodules.

```bash
  git clone https://github.com/tumBAIS/euro-meets-neurips-2022.git
  cd pchgs
```

Step 2- Generating a makefile

```bash
mkdir build
cd build
cmake .. -DCMAKE_BUILD_TYPE="RELEASE"
```

Step 3- Build

```bash
make
```


### Part II - Train ML-CO policy

Step 4- Install the dependencies
```bash 
pip install -r requirements.txt
```
Note - In training configuration `./training/src/config.py` changed "number of training epochs" to 4 to keep the training time short.
Step 5-
```bash 
python run_training.py
```
Step 6- Starting the training 
```bash 
bash master_experiments.sh
``` 



### Part III - Evaluate ML-CO policy

Step 7- Starting evaluating policies.
```bash 
python solve_bound.py
```
Step 8- Identifying the best learning iteration for each trained model.
```bash 
bash master_validation.sh 
```
Step 9- Starting the final test run.
```bash 
bash master_test.sh
```

### Part IV - Visualize results from the paper
Step 10- Visualize the results of the paper.

```bash 
python visualization.py
```
