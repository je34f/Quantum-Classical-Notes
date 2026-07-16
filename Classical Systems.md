- **Operators on bits:**
	- Basic unit of information: Bit 0/1
	- Identity: I(0) = 0, I(1) = 1
   	<img width="924" height="696" alt="image" src="https://github.com/user-attachments/assets/ee18f7f7-cf3e-455b-af38-00f5d4791f26" />
		- If start at Initial state 0, we move up to 0, 0 does not go to 1, hence the null symbol. <img width="814" height="578" alt="image" src="https://github.com/user-attachments/assets/589c8d9b-f255-400b-b2d6-c9d702e11be7" />

	- Not operator (inverts input): NOT(0) = 1, NOT(1) = 0. I.e start with 1, we don't move down to 0 so (0)
		- <img width="718" height="382" alt="image" src="https://github.com/user-attachments/assets/424616d0-5ccf-402f-8ce0-ff2f0cc0708a" />

	- <img width="700" height="516" alt="image" src="https://github.com/user-attachments/assets/5be704e1-ed0d-46d2-88df-11a0effc7fae" />

		- Zero and One operators are opposite, zero always gives 0 as output, one always give 1 as output.
		- Operators can be reversible (easily determine the initial value by checking the final value)
			- NOT/I operators are reversible, but Zero/One operator is not reversible.
- **Coin Flip:**
	- Coin has 2 sides: Heads and Tails
	- We can represent the state by 1 bit: 0 represents heads, 1 represents tails.
	- <img width="842" height="326" alt="image" src="https://github.com/user-attachments/assets/c9e2f24e-6de1-472b-a441-ea6080db270a" />

	- <img width="850" height="512" alt="image" src="https://github.com/user-attachments/assets/8bd407a9-8328-47dd-b34f-5860882d9eea" />

- **Probabilistic States**
  
	- Linear combination of basis vectors with 2 properties:
		- Each coefficient is non-negative.
		- The summation of coefficients is 1.
	- We can show all information as a single mathematical object called a **stochastic vector**.
	- Alternatively, we can say that a probabilistic state is a probability distribution over deterministic states.
	- Suppose that Asja tosses a fair coin secretly.
		- As we do not see the result, our information about the outcome will be **probabilistic**:
			- The outcome is heads with probability 0.3 and the outcome will be tails with probability 0.7 (example).
			- In general, a probabilistic bit is in states 0 and 1 with probabilities p and 1-p, where 0 <= p <= 1. (Note that if p = 0 or p = 1, the bit becomes deterministic.)
			- If the coin has a bias Pr(H)/Pr(T) = 3/1, then the outcome will be heads with probability 0.75 and tails with probability 0.25.
		- We use a column of size 2 to show the probabilities of getting heads and getting tails:
			- <img width="760" height="370" alt="image" src="https://github.com/user-attachments/assets/376ac601-e494-4733-bf8a-68bb47473e2e" />

	- Vector representation:
		- Suppose we have a system with 4 distinguishable states: s1, s2, s3 and s4.
		- We say that the system is in one of the states with probability 1 and any of the other states with probability 0.
		- We can therefore show each state as a column vector, which helps us represent our information when it is in more than 1 state with certain probabilities:
		- <img width="702" height="222" alt="image" src="https://github.com/user-attachments/assets/68fa653a-bd76-4c8d-b10e-fe6e17a04511" />

		- Now, bringing back the case where the coins are tossed secretly:
			- <img width="1140" height="790" alt="image" src="https://github.com/user-attachments/assets/54b084c4-bae6-4def-8f63-7d8431209431" />

- **Probabilistic Operators**:
  
	- Evolves the system from a probabilistic state to a probabilistic state.
	- Can be represented as a square table or a matrix.
	- The entries of a probabilistic operator represents the transition probabilities between the states.
		- 1. Each entry is **non-negative**.
		- 2. Each column represents the transition probabilities from a state to all states, thus **the summation of all entries in each column is 1** (probability 1 is distributed over all states).
	- Any matrix satisfying these 2 properties is called a **stochastic matrix**.
	- **Probabilistic evolution**:
		- A probabilistic state is a stochastic vector, v.
		- A probabilistic operator is a stochastic matrix, A.
		- If a probabilistic operator A is applied to a probabilistic state v, the new state, v', is calculated as:
			- v' = A . v
				- I.e the evolution of a linear system is represented by matrix-vector multiplication.
		- <img width="934" height="368" alt="image" src="https://github.com/user-attachments/assets/f50904fc-aa82-4816-8bb9-1608fa9652a6" />

			- Note that when we are given a probabilistic operator, transitions are from top to left, i.e for 2nd to 3rd state, the transition probability is **0.3**.
			- Transition probability from the 3rd state to the 1st state is **0**.
			- Transition probability from the 1st state to the 2nd state is **0.2**.
- **Two Probabilistic Bits**:
  
	- Suppose we have 2 probabilistic bits and our probabilistic states respectively are: (0.2 0.8) and (0.6 0.4).
	- If we combine both bits into a single system, what is the state of the combined system?
		- We can have 4 different states:
			- 00: Both bits in states 0
			- 01
			- 10
			- 11
	- The vector representation of state 0 is (1 0) and the vector representation of state 1 is (0 1).
	- <img width="1014" height="326" alt="image" src="https://github.com/user-attachments/assets/22887179-5b12-4d1a-8b52-84ac542131b3" />

	- Composite Systems:
		- When 2 systems are composed, then their states are tensored to calculate the state of the composite system.
		- For e.g:
			- <img width="902" height="352" alt="image" src="https://github.com/user-attachments/assets/d9b39d69-382f-4356-a650-b6d8a6231d0e" />

			- Note that tensor product is the circle with an 'x' in the middle. It is used when you combine separate subsystems to form the overall **state** space.
			- Tensor product distributes over addition in the same way as the distribution of multiplication over addition.
			- E.g <img width="720" height="60" alt="image" src="https://github.com/user-attachments/assets/2438916b-5124-4209-92d5-958584084c6c" />

			- <img width="1116" height="292" alt="image" src="https://github.com/user-attachments/assets/9f9722a7-49bc-474e-bdd3-6169e8208da9" />

- **Correlation**:
  
	- Our father prepares the lunches of my sister and mine. He puts our boxes either pasta or couscous salad. Until opening the boxes, we do not know our lunch. But, **once I open my box, I will know the lunch of my sister as well**, and vice versa.
	- Controlled-NOT operator (CNOT): If the state of the first bit (controlled bit) is 1, then the value of the second bit (targeted bit) is **flipped**.
		- CNOT[00] = [00]
		- CNOT[01] = [01]
		- CNOT[11] = [10]
		- CNOT[10] = [11]
	- Correlated systems:
		- If the state of a composite system **cannot** be written as the tensor product of the states of its sub systems, then we can say that the **sub-systems are correlated**.
			- E.g: <img width="1238" height="272" alt="image" src="https://github.com/user-attachments/assets/a8e5dbf1-9e2c-41d2-897f-bef80a89e1c3" />

				- <img width="1132" height="684" alt="image" src="https://github.com/user-attachments/assets/3554b8ca-2394-48dd-8e60-ef831fd204f0" />

		- Observe that the **correlation with a new bit can be created by applying a CNOT gate** between any bit already in the correlation and the new bit, where the new bit is the target one.
			- <img width="1248" height="488" alt="image" src="https://github.com/user-attachments/assets/19cd24fd-9365-499d-9af4-8f01a445c9a6" />

			- How does going from 1111 to 1110 show correlation? Before the CNOT gate was applied, the 4th bit is 1 (in 1111) no matter what the 3rd bit was. The 4th bit thus does not tell you anything about the 3rd bit (they're independent).
			- After the CNOT gate was applied (1111 --> 1110), the 4th bit is now dependent on the 3rd bit (in 0001, 3rd bit = 0, 4th bit = 1, in 1110, the 3rd bit = 1, 4th bit = 0 --> i.e 4th bit = NOT(3rd Bit).)
- **Operators on Multiple Bits**:
  
	- **Single Bit Operators**:
		- When we have 2 bits, then the system has 4 states and any operator of the system can be defined as a (4x4)-dimensional matrix.
		- <img width="1210" height="652" alt="image" src="https://github.com/user-attachments/assets/16e8b924-1c6d-4920-881a-930e766d374c" />

			- For a 2x2 matrix I = (1 0 / 0 1) and any matrix M, the **Kronecker Product** (tensor product specifically for matrices and is a way of combining two matrices of any size into 1 bigger matrix.) is built by **taking each entry of I and replacing it with that entry x the whole matrix M.**
			- Note that M is second in this Kronecker Product because we want M to be applied to the second bit. If we want to apply it to the first bit, we assume I is applied to the second bit (to keep it the same), hence it will then be M x I instead.
				- <img width="1102" height="368" alt="image" src="https://github.com/user-attachments/assets/16a23397-37ea-4fdb-a1a1-9b391f1492cf" />

	- **Two Bit Operators**:
		- <img width="1256" height="418" alt="image" src="https://github.com/user-attachments/assets/b155ec28-5a0a-4d7f-a255-c63e9207a064" />

		- <img width="1240" height="962" alt="image" src="https://github.com/user-attachments/assets/0ec28245-ecf1-4615-bf38-96f89c744572" />

			- Why are the last two transition probabilities zeros in the above table?
				- This is because the last two probabilities reflect a flip in the value of the second-bit from either 0 --> 1 or 1 --> 0, which is impossible given that only the identity operator is being applied to the second-bit (value should not change).
	- **Controlled Operators**:
		- The matrix form of the **controlled-NOT** operator is:
			- <img width="1124" height="242" alt="image" src="https://github.com/user-attachments/assets/5b759697-d1a7-4f2f-b05f-cf5d9afc2c86" />

		- Similarly, for a given single bit operator M, the **controlled-M operator** (first bit is control, second bit is target) is:
			- <img width="336" height="138" alt="image" src="https://github.com/user-attachments/assets/4012bc32-ad4f-4b99-8549-d57ac6357903" />

		- By definition:
			- **When the first bit is 0**, the **identity** is applied to the second bit.
			- **When the first bit is 1**, the **operator M** is applied to the second bit.
			- To illustrate, observe CM above:
				- Since the first bit is the control bit, the value of the first bit never changes, hence the off-diagonal sub-matrices are **zeros**.
				- When the first bit is 0, the identity is applied to the second bit, hence the top-left matrix is **I**.
				- When the first bit is 1, the operator M is applied to the second bit, hence the bottom-right matrix is **M**.
			- <img width="500" height="434" alt="image" src="https://github.com/user-attachments/assets/dc742bcb-a0a9-42bb-acc7-7d9a9d0f01ed" />

				- M acts on a single bit as:
					- M|0> = 0.7|0> + 0.3|1>
					- M|1> = 0.4|0> + 0.6|1>
					- (Remember that the columns of M = images of |0> and |1>)
				- Now, go through the 2-bit basis state, checking bit 2 (control bit):
					- |00>: control bit = 0 -> do nothing -> stays |00>
					- |10>: control bit = 0 -> do nothing -> stays |10>
					- |01>: control bit = 1 -> apply M (tensor product) to bit 1 (which is 0)  -> 0.7|01> + 0.3|11>
				- Now, using column order |00>, |01>, |10>, |11> to get:
					- <img width="530" height="256" alt="image" src="https://github.com/user-attachments/assets/4be5a900-8b06-46bd-b50b-acc79ac818c3" />

	- **Controlled operator activated when in state 0**:
		- Controlled operators are defined to be triggered only when the **control bit is in state 1.** However, in this example, we expect it to be triggered when the **control bit is in state 0**.
		- To do so, we can:
			- Apply NOT-operator to the first bit
			- Apply CM operator
			- Apply NOT-operator once more
		- This guarantees that M is applied to the second bit if **the first bit is in state 0** and do nothing if the first bit is in state 1.
			- <img width="684" height="116" alt="image" src="https://github.com/user-attachments/assets/44c4d5ce-1af9-4365-b806-91f1cd75ff0e" />

				- To help prove:
					- X = (0 1 / 1 0)
