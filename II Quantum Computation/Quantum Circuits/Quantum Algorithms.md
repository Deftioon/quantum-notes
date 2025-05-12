A common saying is that quantum computers can *do more* than a classical computer. This is not the case, a quantum computer has the same "power" as a classical Turing machine. However, some practical problems are impossible to solve on a classical computer not because that it physically  cannot, but rather it would take an astronomical amount of resources to solve that problem. 

The promise of quantum computers is to enable new algorithms to be performed which turn these astronomical problems on classical computers into feasibly solvable problems on quantum computers. Nielsen and Chuang write that there are two classes of quantum algorithms at the time of writing (2010):
- Those based off Shor's *quantum Fourier transform*, which solves for the factoring and discrete logarithm problems, bringing an *exponential* speedup in speed. These algorithms allow a quantum computer to break one of the most used encryption standards, RSA.
- Those based off Grover's algorithm for *quantum search*. These only give slightly less yet still remarkable *quadratic* speedups.  These extract statistics, such as the minimum element in an array of numbers. It can speedup the search for keys to cryptosystems such as the widely used Data Encryption Standard.

There are very few quantum algorithms that are out there, and even few that are practical. This is because the human mind is used to thinking classically, and not in a quantum sense. Developing quantum algorithms requires special insights and tricks.

Read next:  [[Operating on a Single Qubit]]