1. Quantum Circuits Dataset
    Link: https://datadryad.org/stash/dataset/doi:10.5061/dryad.k6t1rj8

    Five scales of quantum circuits, n53m12, n53m14, n53m16, n53m18 and n53m20, are included.
    ![截屏2024-01-06 10 55 48](https://github.com/YangletLiu/RL4QuantumCircuits/assets/75991833/f283e6c0-346a-49ad-b254-851e4595e3f2)

    Select the corresponding 5 Python-format circuit files：
   
           datasets_generator/sycamore/circuit_n53_m12_s0_e0_pABCDCDAB.py
           datasets_generator/sycamore/circuit_n53_m14_s0_e0_pABCDCDAB.py
           datasets_generator/sycamore/circuit_n53_m16_s0_e0_pABCDCDAB.py
           datasets_generator/sycamore/circuit_n53_m18_s0_e0_pABCDCDAB.py
           datasets_generator/sycamore/circuit_n53_m20_s0_e0_pABCDCDAB.py
   
3. Convert circuit files to Tensors and labels with the following items：
https://github.com/Fanerst/simulate_sycamore/tree/main

   You can put datasets_generator/sycamore/Circuit2Tensor.py into the examples folder of the simulate_sycamore project for converting the format of the circuit file.

   The resulting Tensors and Labels files are:

           label_n53_m12.txt
           label_n53_m14.txt
           label_n53_m16.txt
           label_n53_m18.txt
           label_n53_m20.txt
