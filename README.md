# Classical Simulations of Quantum Circuits Using Reinforcement Learning
<!-- ROADMAP -->

## :pencil: Foreword   

:open_mouth: __Who wins in the classical versus quantum computing competition__ ? 
Back in 2019, Google proudly announced “quantum supremacy” with its 53-qubit Sycomore quantum circuits,  which was later challenged by researchers claiming to have pulled ahead of Google on classical computers. We assert that any tech giant, university spinoff, or startup is too hasty to advertise ``quantum supremacy” via quantum circuits on the scale of 50 ～ 100 qubits.  
Thus, __an improved benchmark curve for classical simulations for quantum circuits__ is really important. This is also the reason why we start this project.    

## :dart: Our goal  

By representing the quantum gates as the tensor diagrams, the quantum circuits can be represented by a tensor network. Then, the simulation of quantum circuits actually corresponds to the contraction of the tensor network. Thus, the problem of getting an improved benchmark curve for classical simulations for quantym circuits becomes to find a better contraction order for the tensor network, which has fewer number of multiplications.   

Reinforcement learning (RL) algorithms  have behaved great potential to solve such similar combination problems, such as graph cut, TSP, and so on. [1] also proposed to apply the RL algorithm to find the optimal tensor network contraction order. However, it is not enough to get the benchmark curve, as well as to identify the real “quantum supremacy”.   

__We hope this project can bridge the gap between the quantum circuit and the deep learning, especially the RL community, to work together to find the real “quantum supremacy” and prompt the techniuqe development.__  


## :triangular_flag_on_post: Roadmap  

In our project, we will mainly focus on three aspects, namely the dataset, simulation envrionment, and benchmark,

__Dataset__: We will release various datasets for the tensor representations of quantum circuits, for other researchers to verify their ideas.  
:white_check_mark: Tensor-Train/MPS tensor network  
:white_check_mark: Tensor-Ring tensor network  
:white_check_mark: Tree tensor network  
:white_large_square: PEPS tensor network  
:white_large_square: MERA tensor network  
:white_large_square: Google's Sycamore circuit  

__Simulation environment__: We will develop efficient simulation environments for reserchers to debug their algirithms. For each tensor network, we will develop the single and the parallel version of the simulation environment, respectively. The parallel enviroment will be much more efficient in the data sampling, thus to significantly improve the efficiency of training RL agents.  

|Tensor network| Single| Parallel|   
|-----------------|-------|--------|  
|TT/MPS|:white_large_square:|:white_large_square:|  
|TR|:white_large_square:|:white_large_square:|  
|Tree|:white_large_square:|:white_large_square:|  
|PEPS|:white_large_square:|:white_large_square:|  
|MERA |:white_large_square:|:white_large_square:|  
|Sycamore|:white_large_square:|:white_large_square:|    


__Benchmark__: We will merge and supply widely used algorithms, which has been applied for the classical simulations of quantum circuits, for other researchers to compare their methods' performance.  
:white_check_mark: greey strategy of optimized einsum (OE)  
:white_check_mark: dinamic programming of optimized einsum (OE)  
:white_check_mark: kahypar    
:white_large_square: RL-Hamiltonian      

:wave: We are always welcome other researchers to contribute the benchmark algorithms, including the suggestions of methods, better hyper-parameters, etc., and the datasets, especially the pratical quantum circuits.   




## :clipboard: Experimental Results
### Tensor-Train/MPS tensor network  
![TT](/mps/img/ttmps.png)   

To run the baseline methods, just execute ___"python  cotengra.py"___ or ___"python opt_einsum.py"___, where the variable ___n___ is the number of the tensor network.    
To generate the Tensor-Train/MPS dataset, please execute ___"python mps_generate.py"___, where the variable ___V___ in the ___main___  part is the number of tensor nodes.       

We present the ___Number of multiplications___ versus the ___Number of tensor nodes___ in the tensor-train/mps tensor network in the following table,    

| number of nodes | 10    | 50     | 100    | 200    | 400     | 600     | 800     | 1000    | 1500    | 2000    |    
|-----------------|-------|--------|--------|--------|---------|---------|---------|---------|---------|---------|  
| OE greedy       | 3.848 | 15.875 | 30.927 | 61.030 | 121.236 | 181.442 | 241.648 | 301.854 | X       | X       |  
| OE dynamic      | 3.693 |-------|-------|-------|--------|--------|--------|--------|--------|--------|  
| CTG greedy      | 3.693 | 15.656 | 30.705 | 60.808 | 121.014 | 181.220 | 241.426 | 301.632 | X       | X       |  
| CTG kahypar     | 3.690 | 15.650 | 30.710 | 60.810 | 121.010 | 181.220 | 241.430 | 301.630 | 451.150 | 602.660 |  
| RL-Hamiltonian  |       |        |        |        |         |         |         |         |         |         |  

note: (1) OE dynamic can not give a solution in a limited time for the number of nodes from 50 to 2000.  
(2) OE greedy and CTG greedy can not scale up to the number of nodes 15000 and 2000.  


### Sycamore circuit          

![Sycamore](sycamore/dataset/sycamore.png)

We present the ___Number of multiplications___ versus the ___Number of cycles___ in the sycamore circuit in the following table,    
| number of cycles| 12    | 14     | 16     | 18     | 20      |      
|-----------------|-------|--------|--------|--------|---------|  
| OE greedy       | 17.795| 19.679 | 25.889 | 26.793 | 26.491 |  
| OE dynamic      | ------- |------- |------- |------- |-------- |   
| CTG greedy      | 17.065 | 19.282 | 23.151 | 23.570 | 25.623 |    
| CTG kahypar     | 13.408 | 14.152 | 17.012 | 17.684 | 18.826 |     
| RL-Hamiltonian  |       |        |        |        |         |      


Reference:

[1] Meirom, E., Maron, H., Mannor, S., & Chechik, G. Optimizing tensor network contraction using reinforcement learning. In International Conference on Machine Learning (pp. 15278-15292). ICML 2022.  
[2] Daniel, G., Gray, J., et al. (2018). Opt_einsum-a python package for optimizing contraction order for einsum-like expressions. Journal of Open Source Software, 3(26):753 https://github.com/dgasmith/opt_einsum    
[3] Gray, J. and Kourtis, S. (2021). Hyper-optimized tensor network contraction. Quantum, 5:410. https://github.com/jcmgray/cotengra    
  