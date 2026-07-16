- **First Quantum Programs with Qiskit**:
	- Every reversible classical program (program containing only reversible operators: NOT and Identity) is also a quantum program.
		- We use a **quantum register** to keep our quantum bits: q = QuantumRegister(1, "qreg")
			- To retrieve an information from a quantum bit, it must be **measured**. This measurement result is stored classically, so we also use a **classical register** with classical bits: c = ClassicalRegister(1, "creg").
			- Now, we can define our quantum circuit, which is composed by a quantum and a classical register: qc = QuantumCircuit(q,c)
			- We can apply a NOT operator represented as "x" on Qiskit onto the quantum bits: qc.x(q[0]) --> note that bits are enumerated starting from 0 and NOT operators/x-gates are applied to the **first qubit** of the quantum register.
			- Lastly, measurement is defined by associating a quantum bit to a classical bit: qc.measure(q[0], c[0])
			- To end off, we can then visualise the quantum circuit by drawing it: qc.draw()
	- In quantum computing, state 0 is denoted as |0>. This notation is called a **ket**.
- **Hadamard Operator**:
	- An example quantum operator for quantum coin-flipping is Hadamard, defined as a **h-gate** in Qiskit.
		- Creates **superposition**, taking a qubit in a definite classical state (|0> or |1>) and transforming it into a 50/50 probability mixture of both states.
	- |.> is called **ket-notation**. It is used to represent a column vector in quantum mechanics. For a given column vector |v>, its conjugate transpose (swapping the rows and columns, changing the sign of its imaginary part; denoted as **A^H**) is a row vector represented as <v| (bra-notation).
		- In Qiskit, h-gate is applied as: **qc.h(q[0])**
	- <img width="794" height="618" alt="image" src="https://github.com/user-attachments/assets/1f6a4ba6-ad95-40a8-82c7-9fe8526bf039" />
	
		- Note that when h-gate is applied twice on the qubit (once at each quantum coin-flipping stage), the only outcome must be 0 as the qubit will be returned to its original state **(H² = I)**.
- **One Qubit**:
	- A qubit has two states: 0 and 1.
	- They are denoted by ket-notation: |0> and |1>.
	- **NOT Operator**:
		- Flips the value of a qubit.
    
		- <img width="254" height="134" alt="image" src="https://github.com/user-attachments/assets/ecca8841-83c8-4746-a94e-b9f4342bbc42" />
		- X|0> = X (1 0) = (0 1) = |1>
	- **Hadamard operator**:
		- H looks similar to a fair coin-flipping.
		- <img width="404" height="192" alt="image" src="https://github.com/user-attachments/assets/a8998d16-e164-41b5-b736-16b334efb595" />
		- Note:
			- Quantum systems can have **negative transitions**.
	- **One-step Hadamard**:
		- Start in **|0>**.
		- After applying H:
			- H|0> = $\begin{pmatrix} \frac{1}{\sqrt2} \\ \frac{1}{\sqrt2} \end{pmatrix}$ --> After measurement, we observe the states |0> and |1> with equal probability 1/2, how?
		- Now start in **|1>**.
		- After applying H:
			- H|1> = $\begin{pmatrix} \frac{1}{\sqrt2} \\ \frac{-1}{\sqrt2} \end{pmatrix}$ --> After measurement, we still observe the states |0> and |1> with equal probability 1/2 even when one of the values is negative.
		- **The square of a negative value is also positive.**
			- When a quantum system is measured, the probability of observing one state is the **square of its value**.
			- The value of the system being in a state is called its **amplitude**.
			- In the above examples, the amplitudes of states |0> and |1> are $\frac{1}{\sqrt2}$ and $\frac{-1}{\sqrt2}$ respectively.
				- Since the probability of observing one state is the square of its value, the probability of observing them after a measurement is 1/2 (Note that after observing state 0, the new state is |0>, and after observing state 1, the new state will be |1>.)
				- <img width="1180" height="244" alt="image" src="https://github.com/user-attachments/assets/ab642d9c-91db-4f98-912d-21674bcf0bc6" />
				
					- For example, probability of observing state |0> and |1> if system is in $\begin{pmatrix} \frac{-3}{5} \\ \frac{-4}{5} \end{pmatrix}$ is 9/25 and 16/25 respectively, which is the exact same for if system is in $\begin{pmatrix} \frac{3}{5} \\ \frac{-4}{5} \end{pmatrix}$ . This shows that the sign does not matter, only magnitude. Note that 9/25 + 16/25 = 1.
		- States |+> and | - >:
			- The quantum states obtained after applying H to |0> and |1> are known as **ket-plus** and **ket-minus** respectively.
				- |+> = H|0> = $\begin{pmatrix} \frac{1}{\sqrt2} \\ \frac{1}{\sqrt2} \end{pmatrix}$
				- | - > = H|1> = $\begin{pmatrix} \frac{1}{\sqrt2} \\ \frac{-1}{\sqrt2} \end{pmatrix}$
		- **For a valid quantum state, compute the sum of the squared magnitudes of the entries. If it's 1, it's valid. Else, normalize it by dividing every entry by the vector's norm (square root of that sum).**
			- E.g for a single qubit |psi> = a|0> + b|1>, if a = 1 and b = 1   -> |1|² + |1|² = 2 != 1 -> this is an invalid quantum state.
- **Quantum State**:
	- Overall probability must be 1 when we observe a quantum state (See *One Qubit*).
		- E.g: $\begin{pmatrix} \frac{1}{2} \\ \frac{1}{2} \end{pmatrix}$ **cannot** be a valid quantum state as the overall probability of observing states |0> and |1> is 1/4 + 1/4 = 1/2 != 1.
	- **Formally, a quantum state can be represented by a vector having length 1, and vice versa.**
		- The summation of amplitude squares gives the **square of the length of the vector**.
		- Remember that length of vector ||u|| = sqrt(u . u) -> In quantum computation, we use **inner product** instead of dot product (defined on complex numbers).
			- By using bra-ket notation, **|| |u> || = sqrt(<u|u>) = 1** OR **<u|u> = 1**, where <u|u> is the short form of <u||u>.
	- Quantum Operators:
		- Now that we have defined the quantum state, the definition of quantum operator is easy: **Any length-preserving (square) matrix is a quantum operator,** and vice versa.
- **Visualisation of a (Real-Valued) Qubit**:
	- Suppose we have a single qubit. Each possible (real-valued) quantum state of this qubit is a point on 2-dimensional space.
	- It (quantum state) can also be represented as a vector from origin to that point.
		- We start with the visual representation of the following quantum states:
			- |0> = $\begin{pmatrix} 1 \ & 0 \end{pmatrix}$ , |1> = $\begin{pmatrix} 0 \ & 1 \end{pmatrix}$ , -|0> = $\begin{pmatrix} -1 \ & 0 \end{pmatrix}$ , -|1> = $\begin{pmatrix} 0 \ & -1 \end{pmatrix}$ .
		- We draw these quantum states as points, and we use "draw_axes()" to draw axes. We include this predefined function via the following line: "**%run quantum.py**":
			-
			  ```from
			  figure(figsize=(6,6), dpi=80) 
			  
			  %run quantum.py
			  
			  draw_axes()
			  
			  plot(0,0,'ro') # a point in red color 
			  
			  plot(1,0,'bo') 
			  plot(0,1,'go')
			  plot(-1,0,'yo')
			  plot(0,-1,'co')
			  
			  show()
			  ```
			- <img width="906" height="830" alt="image" src="https://github.com/user-attachments/assets/d87b21db-245b-4194-ba8f-fc1308848ef7" />
			
	- **Unit Circle**:
		- All (real-valued) quantum states of a qubit form the unit circle.
		- The length of each quantum state is 1.
		- All points that are 1 unit away from the origin form the circle with radius 1 unit.
			- Can be done in Qiskit via the function: "draw_unit_circle()"
	- **Quantum state of a qubit**:
		- Suppose we have a single qubit. Each possible (real-valued) quantum state of this qubit is a point on a 2-D space.
		- It can also be represented as a vector from origin to that point.
		- <img width="762" height="830" alt="image" src="https://github.com/user-attachments/assets/59918c51-3131-42f5-9103-47c727fd448b" />
		
			- draw_qubit() -> draws a figure, the origin, the axes, the unit circle and the base quantum states.
			- draw_quantum_state(x,y,name) -> draws an arrow from (0,0) to (x,y) and associates it with name.
		- We can also draw the vector's angle with the axes and its projection on both axes:
			-
			  ```%run
			  draw_qubit()
			  
			  draw_quantum_state(3/5,4/5,"|v>")
			  
			  from matplotlib.pyplot import arrow, text, gca 
			  
			  # the projection on |0>-axis
			  arrow(0,0,3/5,0,color="blue",linewidth=1.5)
			  arrow(0,4/5,3/5,0,color="blue",linestyle='dotted')
			  text(0.1,-0.1,"cos(a)=3/5") 
			  
			  #the projection on |1>-axis:
			  arrow(0,0,0,4/5,color="blue",linewidth=1.5)
			  arrow(3/5,0,0,4/5,color="blue",linestyle='dotted')
			  text(-0.1,0.55,"sin(a)=4/5",rotation=90) drawing the angle with |0>-axis
			  
			  from matplotlib.patches import Arc
			  gca().add_patch( Arc((0,0),0.4,0.4,angle=0,theta1=0,theta2=53) )
			  text(0.08,0.05,'.',fontsize=30)
			  text(0.21,0.09,'a')
			  ```
			- <img width="774" height="674" alt="image" src="https://github.com/user-attachments/assets/e017d23d-d18d-492a-b2ac-3a5583e419a7" />
			
			- What does this show?
				- Angle of quantum state with state |0> is a
				- Amplitude of state |0> is cos(a) = 3/5
				- The probability of observing state |0> is cos²(a) = 9/25
				- The amplitude of state |1> is sin(a) = 4/5
				- The probability of observing state |1> is sin²(a) = 16/25
	- **The angle of a quantum state**:
		- The angle of a vector (radians) on the unit circle is the length of the arc in **counter-clockwise direction** that starts from (1,0) and with the points representing the vector.
	- **Random quantum states**:
		- **Any quantum state of a (real-valued) qubit is a point on the unit circle.**
		- We use this fact to create random quantum states by picking a random point on the unit circle.
- **Superposition**:
	- Suppose A starts in $\begin{pmatrix} 1 \ & 0\end{pmatrix}$ and **secretly** applies the probabilistic operator $\begin{pmatrix} 0.3  & 0.6 \ & 0.7  & 0.4 \end{pmatrix}$ . Since she applied her operator secretly, our information about her state is probabilistic, which is calculated as:
		- <img width="442" height="162" alt="image" src="https://github.com/user-attachments/assets/f4d2d97e-285a-4974-aae5-cf67e0bff018" />
		
		- A is **either in state 0 or in state 1.**
		- However, from OUR POV, A is in state 0 with probability 0.3 and in state 1 with probability 0.7 -> A is in a **probability distribution** of states 0 and 1, **being in both states at the same time** but with different weights.
		- **On the other hand, if we observe A's state, then our information about A becomes deterministic: either (1 0) or (0 1). Hence, we can say that after observing A's state, the probabilistic state (0.3 0.7) collapses to either (1 0) or (0 1).**
	- <img width="844" height="592" alt="image" src="https://github.com/user-attachments/assets/d585dbb5-1ac0-47d3-bc07-a5e758ed7747" />
	
		- The photon is initially in state |v0> = (1 0)
		- Step 1: Hadamard is applied onto |v0> -> |v1> = ( 1/sqrt2 1/sqrt2)
			- The photon is in a **superposition of state |0> and state |1>**, being in both states with the amplitudes 1/sqrt2 and 1/sqrt2 respectively.
			- The state of the photon is |v1> = $\begin{pmatrix} \frac{1}{\sqrt2} \\ \frac{1}{\sqrt2} \end{pmatrix}$ , which we can represent as: |v1> = $\frac{1}{\sqrt2}$ |0> + $\frac{1}{\sqrt2}$ |1>.
		- Step 2: Hadamard is applied again
			- H|0> = $\frac{1}{\sqrt2}$ |0> + $\frac{1}{\sqrt2}$ |1> (transition amplitudes of the first column)
			- H|1> = $\frac{1}{\sqrt2}$ |0> - $\frac{1}{\sqrt2}$ |1> (transition amplitudes of the second column)
			- Lastly, effect of Hadamard applied on the quantum state |v1>: |v2> = H|v1> = $\frac{1}{\sqrt2}$ H|0> + $\frac{1}{\sqrt2}$ H|1>
			- Substituting the H|0> and H|1> values into |v2>: ( $\frac{1}{2}$ + $\frac{1}{2}$ )|0> + ( $\frac{1}{2}$ - $\frac{1}{2}$ )|1> = |0> -> **This explains why state |1> disappears**.
		- The amplitude of |0> becomes 1 but the amplitude of |1> becomes 0 because of cancellation.
			- After the second Hadamard, the outcomes are **interfered with each other**, which can be constructive or destructive. In this example, the outcome |0> are interfered constructively, but the outcome |1> are interfered destructively.
	- **Observations**:
		- Probabilistic systems: If there is a nonzero transition to a state, then it contributes to the probability of this state positively.
			- e.g: Say state **A** is reached from two other states, **X** and **Y**, with these transition probabilities:
				- X → A with probability 0.5
				- Y → A with probability 0.3
			- If X currently holds probability 0.4 and Y holds 0.6, the contributions to A are:
				- from X: 0.4 × 0.5 = 0.20
				- from Y: 0.6 × 0.3 = 0.18
				    
				  Total probability at A = 0.20 + 0.18 = **0.38**  
				    
				  Every nonzero transition adds to the total. You never need to know the other transitions to know that a given one *helps* — a nonzero contribution is always a positive contribution.  
		- Quantum systems: If there is a nonzero transition to a state, then we cannot know its contribution without knowing the other transitions to this state (e.g a nonzero transition from 
		  |0> to |1> does not tell anything on its own --- whether it ends up constructively/destructively interfering depends entirely on the phase of the other contributions, **which you can't know without looking at all of them**.)  
		- If there is only 1 transition, then it contributes to the amplitude and probability of the state regardless of whether the sign of the transition is positive or negative. If there is >1 transition, then depending on the summation of all transitions, we can determine whether a specific transition contributes or not.
	- **Being in a superposition**:
		- A quantum system can be in more than 1 state with nonzero amplitudes. Then, we can say that our system is in a superposition of these states.
			- When evolving from a superposition, the resulting transitions may affect each other constructively and destructively due to **opposite sign transition amplitudes**.
			- Otherwise, all nonzero transitions are added up to each other as in probabilistic systems.
	- **Measurement**:
		- We can measure a quantum system, then the system is observed in one of its states.
		- The probability of the system to be observed in a specific state is the square value of its amplitude.
			- If the amplitude of a state is **zero**, then this state **cannot be observed.**
			- If the amplitude of a state is **nonzero**, then this state **can be observed**.
		- e.g: if the system is in quantum state $\begin{pmatrix} \frac{-\sqrt2}{\sqrt3} \\ \frac{1}{\sqrt3} \end{pmatrix}$ , then after a measurement, we can observe the system in state |0> with probability $\frac{2}{3}$ and in state |1> with probability $\frac{1}{3}$ .
	- **Collapsing**:
		- After the measurement, the system **collapses to the observed state**, and so the system is no longer in a superposition. Thus, the information kept in a superposition is lost.
			- In the above example, when the system is observed in state |0>, then the new state becomes $\begin{pmatrix} {1}\ & {0} \end{pmatrix}$ .
			- If it is observed in state |1>, then the new state becomes $\begin{pmatrix} {0} \ & {1} \end{pmatrix}$ .
	- **The second experiment of the quantum coin-flipping**:
		- <img width="838" height="602" alt="image" src="https://github.com/user-attachments/assets/b82bfa6b-0bc6-4bc4-8480-a1f80bbc9f04" />
		
		- In this experiment, we make a measurement after the first quantum coin-flipping. If the measurement outcome is in state |0>, then we apply a second Hadamard.
		- The first Hadamard: 
			- We start in state |0> = $\begin{pmatrix} {1} \ & {0} \end{pmatrix}$
			- Next, we apply Hadamard operator -> H|0>
		- The first measurement:
			- Due to the photon detector A, the photon cannot be in superposition, and so it forces the photon to be observed in state |0> or state |1>. This is a measurement.
			- Since the amplitudes are $\frac{1}{\sqrt2}$ , we observe each state with equal probability $\frac{1}{2}$ .
			- Thus with probability $\frac{1}{2}$ , the new quantum state is |0> and |1> each.
		- The second Hadamard:
			- If the photon is in state |0>, then another Hadamard operator is applied. I.e with probability $\frac{1}{2}, the computation continues and another Hadamard is applied.
		- The second measurement:
			- Due to photon detectors B1 and B2, we make another measurement.
			- Thus, we observe state |0> with probability $\frac{1}{4}$ and state |1> with probability $\frac{1}{4}$ . At the end, the state |0> can be observed with probability $\frac{1}{4}$ and the state |1> can be observed with probability $\frac{3}{4}$ .
		
- **Operations on the Unit Circle**:
	- **Initialize a (real-valued) qubit with an arbitrary state**:
		- A qubit is set to state |0> at the beginning. Any real-valued quantum state is a point in the unit circle, and it can be described by an angle $\theta$
			- For $\theta$ $\in$ [0, 2 $\pi$ ), the quantum state is |v> = $\begin{pmatrix} {cos\theta} \ & {sin\theta} \end{pmatrix}$
			- We can set the qubit to the state |v> by using a **rotation operator** between |0> and |1> with angle $\theta$
	- **Rotations with ry-gate**:
		- In Qiskit, ry-gate is used for rotations on the unit circle.
		- Default direction of rotation is **counterclockwise**.
			- quantum_circuit.ry(2 * angle_of_rotation,qubit)
			- Why do we multiple angle of rotation by 2 ? This is because ry-gate is **defined on Bloch sphere**. The states |0> and |1> are placed on the North and South poles of the Bloch Sphere (see below), so the angle between them is $\pi$ . On the other hand, the angle between the states |0> and |1> on the unit circle is $\frac{\pi}{2}$ . Thus, when using the ry-gate, we provide twice of $\theta$ for a rotation with angle $\theta$ on the unit circle.
			- <img width="524" height="608" alt="image" src="https://github.com/user-attachments/assets/c039f68c-feb1-47e7-8691-1a2bff61bb82" />
			
- **Rotations**:
	- <img width="1220" height="828" alt="image" src="https://github.com/user-attachments/assets/65240726-41a6-4f20-bf7b-7b1523cd654d" />
	
	- Any 2D rotation by angle $\theta$ has the fixed form R( $\theta$ ) = $\begin{pmatrix} {cos\theta}  & {-sin\theta} \ & {sin\theta}  & {cos\theta} \end{pmatrix}$ , and the matrix is completely determined by the single unknown $\theta$
	- As such, since we start in state |0> and end in state +>, the applied rotation operator to |0> will be $\begin{pmatrix} {cos\theta} \ & {sin\theta} \end{pmatrix}$ , and $\theta$ = $\frac{\pi}{4}$ to get |+>.
	- Thus, if we apply the same operator again, it is the same as rotating by $\frac {\pi}{4}$ + $\frac {\pi}{4}$ = $\frac {\pi}{2}$ radians total, which will yield B: |1> as the solution.
- **Reflections**:
	- Z-gate (operator):
		- $\begin{pmatrix} {1}  & {0} \ & {0}  & {-1} \end{pmatrix}$
		- Consider the new quantum state |u> = $\begin{pmatrix} {\frac{3}{5}} \ & {\frac{4}{5}} \end{pmatrix}$ . Applying Z to it: |u'> = Z|u> = $\begin{pmatrix} {\frac{3}{5}} \ & {\frac{-4}{5}} \end{pmatrix}$ .
		-
		- Operator Z is a reflection and **its line of reflection is the x-axis**.
		- Note that applying the same reflection twice on the unit circle does not make any change.
	- Hadamard Operator:
		- **It is a reflection operator** and its line of reflection is the line obtained by rotating x-axis with $\frac{\pi}{8}$ radians in counter-clockwise direction.
		- <img width="658" height="622" alt="image" src="https://github.com/user-attachments/assets/e5a64b4d-8418-48f5-8a9e-4a4fbd996004" />
		
	- Reflection Operators:
		- <img width="1248" height="972" alt="image" src="https://github.com/user-attachments/assets/01c66d98-a867-4904-918f-c0b7890373f9" />
	
- **Quantum Tomography**:
	- Similar to learn the bias of a coin by collecting statistics from tossing the coin many times. But, only making measurements may not be enough to make a good guess.
	- <img width="1234" height="756" alt="image" src="https://github.com/user-attachments/assets/7a4bdb8e-5e39-4b7a-b314-49e304a87ad9" />
	
- **Two Qubits**:
	- <img width="1200" height="470" alt="image" src="https://github.com/user-attachments/assets/3efd29c8-bd1f-4df8-bd08-83b72e61751d" />
	
	- Generalization: Suppose that we have k > 1 qubits/bits. Then, any deterministic (basis) state can be represented by k bits: |b1b2...bk>, where any bj $\in$ {0,1} for 1 $\le$ j $\le$ k.
		- The size of the vector representing the states of k qubits = $2^k$
		- If the decimal value of | $b_1$ $$ $b_2$ ... $b_k$ > is b, then the **entry that has the value of 1 will be the entry with index b**.
	-
	- **Unitary backend**:
		- Unitary_simulator gives a single matrix representation of all gates in the circuit until that point.
		- job = UnitarySimulator().run(qc)
		  current_unitary = job.result().get_unitary(circuit, decimals=3).data  
		  print(current_unitary)  
	- **Applying Hadamards to both qubits**:
		- Applying a h-gate to the first and second qubits is the same as applying the following single operator on both qubits:
		- <img width="1182" height="262" alt="image" src="https://github.com/user-attachments/assets/5b164a5b-1aab-4e27-a674-95dcf06e0849" />
		
		- To calculate $H^{\otimes2}$ |00>, we can do it through 3 ways:
			- Direct matrix-vector multiplication
			- Calculate the quantum state of each state then find the quantum state of the composite system (H|0> $\otimes$ H|0>)
			- Make calculations with |0> and |1>
	- **CNOT Operator**:
		- <img width="1230" height="916" alt="image" src="https://github.com/user-attachments/assets/8a83943d-464b-4243-8388-22a0e49c1664" />
		
	- **cx-gate**:
		- CNOT operator is represented as cx-gate in Qiskit (qc.cx(1,0))
		- It takes two arguments: controller-qubit and target-qubit.
		- x-gate (NOT operator) is applied to the target qubit that is controlled by the controller-qubit.
- **Phase Kickback**:
	- We apply a Controlled-NOT operator, but the controller qubit will be affected.
	- Effect of CNOT:
		- The quantum state of the **up qubit (|0>)** before CNOT: |0> -H> $\frac{1}{\sqrt2}$ |0> + $\frac{1}{\sqrt2}$ |1>
		- The quantum state of the down qubit (|1>) before CNOT: |1> -H> $\frac{1}{\sqrt2}$ |0> - $\frac{1}{\sqrt2}$ |1>
		- The quantum state of the composite system: ( $\frac{1}{\sqrt2}$ |0> + $\frac{1}{\sqrt2}$ |1>) ⊗ ( $\frac{1}{\sqrt2}$ |0> - $\frac{1}{\sqrt2}$ |1>)
		- CNOT affects when the **up qubit** has the value 1.
		- Let's rewrite the composite state as below to explicitly represent the effect of CNOT:
			- <img width="1200" height="522" alt="image" src="https://github.com/user-attachments/assets/bf7673f4-4890-426a-b0d7-e8a5ed7ca210" />
			
			- **X-gate (CNOT) swaps the coefficients of |0> and |1>, not just the signs!** Common misconception is that the negative sign for |1> state is swapped to positive after CNOT, but in actual fact it is the entire coefficient of |0> that is now swapped to |1>.
		- Before CNOT operator, the sign of |1> in the up qubit is positive (+ $\frac{1}{\sqrt2}$ ). After CNOT operator, its sign changes to negative (- $\frac{1}{\sqrt2}$ ). This is called **phase kickback**.
	- After CNOT:
		- The quantum states of the qubits are separable (no correlation): <img width="666" height="148" alt="image" src="https://github.com/user-attachments/assets/5bed6957-7087-40eb-be07-3a9b5ca77299" />
		
		- If we apply Hadamard to each qubit, both qubits evolve to state |1>. Thus, **the final state is |11>**.
	  
- **Entanglement and Superdense Coding**:
	- A has a qubit initially set to |0>
	- B has a qubit initially set to |0>
	- **Entanglement**:
		- A applies Hadamard operator to her qubit and the quantum state of A's qubit is now $\begin{pmatrix} \frac{1}{\sqrt2} \\ \frac{1}{\sqrt2} \end{pmatrix}$ .
		- Then, A and B combine their qubits. Their quantum state is now $\begin{pmatrix} \frac{1}{\sqrt2} \\ \frac{1}{\sqrt2} \end{pmatrix}$ ⊗ $\begin{pmatrix} {1} \ & {0} \end{pmatrix}$ = $\begin{pmatrix} \frac{1}{\sqrt2} \ & 0 \\ \frac{1}{\sqrt2} \ & 0 \end{pmatrix}$
		- A and B then apply CNOT operator on 2 qubits. The new quantum state is now $\begin{pmatrix} {1} & {0} & {0} & {0} \ & {0} & {1} & {0} & {0} \ & {0} & {0} & {0} & {1} \ & {0} & {0} & {1} & {0} \end{pmatrix}$ $\begin{pmatrix} \frac{1}{\sqrt2} \ & 0 \\ \frac{1}{\sqrt2} \ & 0 \end{pmatrix}$ = $\begin{pmatrix} \frac{1}{\sqrt2} \ & 0 \ & 0 \\ \frac{1}{\sqrt2}  \end{pmatrix}$ = $\frac{1}{\sqrt2}$ |00> + $\frac{1}{\sqrt2}$ |11>
		- At this moment, A and B's qubits **are correlated to each other.**
		- Now, suppose that A observes her qubit secretly:
			- When A sees the result |0>, then B's qubit also collapses to state |0>. B cannot observe state |1>. This can be explained by looking at the new quantum state which **only contains the 2 basis states |00> and |11>** (the mixed terms |01> and |10> have 0 amplitude.). If A sees |0> as her qubit, which happens with probability $\frac{1}{2}$ , B's qubit is guanrateed to be 0 as well.
			- When A sees the result |1>, then B's qubit also collapses to state |1>. B cannot observe state |0>.
			- This also explains why they are correlated -- the individual outcomes are random but they are not independent of each other.
		- Experimental results have confirmed that this happens even if there is a physical distance between A and B's qubits.
		- It seems correlated quantum particles can "affect each other" instantly, even if they are in different parts of the universe.
		- **If two qubits are correlated in this way, we say that they are entangled.**
		- Note:
			- If the quantum state of two qubits **can be written** as  $\ket{u}$ ⊗ $\ket{v}$ (also known as product states), then two qubits are not correlated, where $\ket{u}$ and $\ket{v}$ are the quantum states of the first and second qubits.
				- this will produce the mixed terms |01> and |10>
				- For a general state a|00> + b|01> + c|10> + d|11>, it is a product state if and only if **ad = bc**.
			- On the other hand, if the quantum state of two qubits **cannot be written** as $\ket{u}$ ⊗ $\ket{v}$ , then there is an entanglement between the qubits.
	- **Quantum communication**:
		- After having the entanglement, B takes his qubit and goes away.
		- A will send 2 classical bits of information by only sending her qubit.
		- <img width="1250" height="672" alt="image" src="https://github.com/user-attachments/assets/03f24b4b-f8b3-4764-8d2d-bb2d3ff48480" />
		
		- Now we describe:
			- A has 2 bits of classical information: a,b ∈ {0,1}
			- There are 4 possible values for this pair (a,b): (0,0), (0,1), (1,0) or (1,1)
			- If a is 1, then A applies Z-gate (i.e $\begin{pmatrix} {1} & {0} \ & {0} & {-1} \end{pmatrix}$ ) to her qubit
			- If b is 1, then A applies x-gate (NOT operator) to her qubit
			- Then, A sends her qubit to B
		- After communication:
			- B has both qubits
			- B applies cx-gate (CNOT operator), where **A's qubit is the controller**
			- B applies H-gate to A's qubit
			- B measures both qubits
			- The measurement result will be exactly (a,b)
	- Verify each case by tracing the state vector (on paper).
		- Now, we need to prove that the above protocol does indeed produce a final measurement that exactly reproduces the original (a,b):
			- By convention, we will write states as |A,B>, i.e |AB>.
			- Build the Bell pair (same for all 4 cases):
				- Start: |00>, Apply H to A's qubit:
					- $\frac{1}{\sqrt2}(\ket0 + \ket1)$ ⊗ $\ket0$ = $\frac{1}{\sqrt2}(\ket{00} + \ket{10})$
				- Apply cx-gate as CNOT(A,B):
					- $\ket{00}$ --> $\ket{00}$ , $\ket{10}$ --> $\ket{11}$
					- $\frac{1}{\sqrt2}(\ket{00} + \ket{10})$ $\Rightarrow$ $\frac{1}{\sqrt2}$ ( $\ket{00}$ + $\ket{11}$ )
			- A encodes with Z and X:
				- (0,0) --- do nothing: $\frac{1}{\sqrt2}$ ( $\ket{00}$ + $\ket{11}$ )
				- (1,0) --- apply Z to A (Z $\ket{0}$ = $\ket0$ , Z $\ket1$ = - $\ket1$ ): $\frac{1}{\sqrt2}$ ( $\ket{00}$ - $\ket{11}$ )
				- (0,1) --- apply X to A (swap 0 ↔ 1 on qubit A): $\frac{1}{\sqrt2}$ ( $\ket{10}$ + $\ket{01}$ )
				- (1,1) --- apply Z then X to A: $\frac{1}{\sqrt2}$ ( $\ket{10}$ - $\ket{01}$ )
			- B decodes (CNOT then H on A) for each case:
				- **(0,0)**: $\frac{1}{\sqrt2}$ ( $\ket{00}$ + $\ket{11}$ ) 
				    
				  CNOT(A → B): $\ket{11}$ → $\ket{10}$ , giving $\frac{1}{\sqrt2}$ ( $\ket{00}$ + $\ket{10}$ ) = $\frac{1}{\sqrt2}$ ( $\ket{0}$ + $\ket{1}$ ) $_A$ ⊗ $\ket0$ $_B$  
				    
				  H on A: → $\ket0$ $_A$ $\ket0$ $_B$  → measure 00 ✓  
				- **(1,0)**: $\frac{1}{\sqrt2}$ ( $\ket{00}$ - $\ket{11}$ )
				    
				  CNOT: $\frac{1}{\sqrt2}$ ( $\ket{00}$ - $\ket{10}$ ) = $\frac{1}{\sqrt2}$ ( $\ket{0}$ - $\ket{1}$ ) $_A$ ⊗ $\ket0$ $_B$  
				    
				  H on A: → $\ket1$ $_A$ $\ket0$ $_B$  → measure 10 ✓  
				- **(0,1)**: $\frac{1}{\sqrt2}$ ( $\ket{10}$ + $\ket{01}$ )
				    
				  CNOT:  $\ket{10}$ → $\ket{11}$ , $\ket{01}$ unchanged, giving $\frac{1}{\sqrt2}$ ( $\ket{01}$ + $\ket{11}$ ) = $\frac{1}{\sqrt2}$ ( $\ket{0}$ + $\ket1$ ) $_A$ ⊗ $\ket1$ $_B$  
				    
				  H on A: → $\ket0$ $_A$ $\ket1$ $_B$  → measure 01 ✓  
				- **(1,1)**: $\frac{1}{\sqrt2}$ ( $\ket{10}$ - $\ket{01}$ )
				    
				  CNOT: $\frac{1}{\sqrt2}$ ( $\ket{11}$ - $\ket{01}$ ) = $\frac{1}{\sqrt2}$ ( $\ket{1}$ - $\ket0$ ) $_A$ ⊗ $\ket1$ $_B$ = - $\frac{1}{\sqrt2}$ ( $\ket0$ - $\ket1$ ) $_A$ ⊗ $\ket1$ $_B$  
				    
				  H on A: → $\ket1$ $_A$ $\ket1$ $_B$  → measure 11 ✓ (the global minus sign does not affect measurement probabilities)  
			- In summary, all 4 cases reproduce (a,b) exactly, confirming that the protocol is correct -- superdense coding works as the pre-shared entanglement + 1 qubit sent lets B recover 2 classical bits.
			  
- **Quantum Teleportation**:
	- A wants to send a qubit to B by using **only classical communication**.
	- Let $\ket{v}$ = $\begin{pmatrix} {a} \ & {b} \end{pmatrix}$ ∈ $\mathbb{R}$ $^2$ be the quantum state.
	- If A has many copies of this qubit, then she can collect the statistics based on these qubits and obtain an approximation of a and b respectively. After this, A can send those approximations using classical bits, the number of which depends on the precision of the amplitudes.
		- This is Quantum Tomography in action.
	- On the other hand, if A and B share the entangled qubits in the state $\frac{1}{\sqrt2}$ $\ket{00}$ + $\frac{1}{\sqrt2}$ $\ket{11}$ in advance, then it is possible for B to create $\ket{v}$ in his qubit after receiving 2 bits of information from A. To explain:
		- **Setup**: A has a qubit in the unknown state $\ket{v}$ = a $\ket{0}$ + b $\ket{1}$ that she wants to get to B, but she can only send **classical bits**. To do this, they pre-share an entangled pair: $\ket{\phi^+}$ = $\frac{1}{\sqrt2}$ $\ket{00}$ + $\frac{1}{\sqrt2}$ $\ket{11}$ ( $\ket{\phi^+}$ is known as a maximally entangled two-qubit Bell state). A holds a qubit of this pair (called A $_2$ ), B holds the other (B $_2$ ). A also holds the qubit that she wants to send (A $_1$ in state $\ket{v}$ ).
			- Why can A only send classical bits ? Because A cannot just "look at" her qubit and see a and b. The only thing she can do is to **measure it**, but measurement is **destructive** --- once you measure, the superposition collapses and the qubit becomes either $\ket{0}$ or $\ket{1}$ . Furthermore, measurement is **probabilistic and gives only 1 bit** --- a single measurement in the standard basis gives outcome 0 with probability a² or outcome 1 with probability b². It does not tell you the actual values a and b!
		- Write the joint state of all 3 qubits
			- $\ket{\psi}$ = $\ket{v}$ $_{A_1}$ ⊗ $\ket{\psi^+}$ $_{A_2B}$ = $\frac{1}{\sqrt2}$ [a $\ket{000}$ + a $\ket{011}$ + b $\ket{100}$ + b $\ket{111}$ ]
			- Group by A's 2 qubits ( $A_1$ $A_2$ ), keeping B's qubit as a "tag" (see below for explanation): $\ket{\psi}$ = $\frac{1}{\sqrt2}$ [ $\ket{00}$ (a $\ket{0}$ ) + $\ket{01}$ (a $\ket{1}$ ) + $\ket{10}$ (b $\ket{0}$ ) + $\ket{11}$ (b $\ket{1}$ )]
			- <img width="454" height="450" alt="image" src="https://github.com/user-attachments/assets/513a1775-8e7e-45b2-ad86-0a6f052833a8" />
			
		- Re-express A's 2 qubits in the Bell basis
			- **Using the identities:**
				- $\ket{00}$ = $\frac{1}{\sqrt2}$ ( $\ket{\Phi^+}$ + $\ket{\Phi^-}$ ) = I
				- $\ket{11}$ = $\frac{1}{\sqrt2}$ ( $\ket{\Phi^+}$ - $\ket{\Phi^-}$ ) = XZ
				- $\ket{01}$ = $\frac{1}{\sqrt2}$ ( $\ket{\Psi^+}$ + $\ket{\Psi^-}$ ) = X
				- $\ket{10}$ = $\frac{1}{\sqrt2}$ ( $\ket{\Psi^+}$ - $\ket{\Psi^-}$ ) = Z
			- $\ket{\psi}$ = $\frac{1}{2}$ [ $\ket{\Phi^+}$ (a $\ket{0}$ + b $\ket{1}$ ) + $\ket{\Phi^-}$ (a $\ket{0}$ - b $\ket{1}$ ) + $\ket{\Psi^+}$ (a $\ket{1}$ + b $\ket{0}$ ) + $\ket{\Psi^-}$ (a $\ket{1}$ - b $\ket{0}$ )] ---(1)
		- A measures her 2 qubits in the Bell basis
			- Each of the 4 outcomes occurs with probability $\frac{1}{4}$ and collapses B's qubit to one of:
				- <img width="992" height="476" alt="image" src="https://github.com/user-attachments/assets/e4fd2ad0-42fd-46b9-a674-757e892a33c9" />
				
					- A's outcomes are the **4 Bell states**:
						- $\ket{\Phi^+}$ = $\frac{1}{\sqrt2}$ ( $\ket{00}$ + $\ket{11}$ )
						- $\ket{\Phi^-}$ = $\frac{1}{\sqrt2}$ ( $\ket{00}$ - $\ket{11}$ )
						- $\ket{\Psi^+}$ = $\frac{1}{\sqrt2}$ ( $\ket{01}$ + $\ket{10}$ )
						- $\ket{\Psi^-}$ = $\frac{1}{\sqrt2}$ ( $\ket{01}$ - $\ket{10}$ )
				- To explain how we derive B's qubit from A's outcome, we look at (1):
					- (1) is a sum of 4 terms and each term is a product of (a specific Bell state on A's two qubits) ⊗ (a specific single-qubit state on B's qubit).
					- If A's measurement outcome is Φ $^+$ (probability $\frac{1}{4}$ ), then the $\ket{\Phi^+}$ term is the one that "happened", and B's qubit -- which was sitting right next to it in that term -- **collapses to** a $\ket{0}$ + b $\ket{1}$ , which is $\ket{v}$ itself. This applies for the other 3 outcomes.
				- Notice in every case, B's qubit is exactly $\ket{v}$ up to a simple, known correction (one of I,X,Z,XZ -- Pauli operators).
		- Classical communication + correction
			- A's measurement outcome is just **2 classical bits** (one of 4 possibilities). She sends these 2 bits to B. Depending on which pair he receives, B applies I, X, Z or XZ to his qubit -- and it becomes exactly $\ket{v}$ , **regardless of what a and b actually are.**
				- Why is A's outcome 2 classical bits specifically?
					- Because A's Bell-basis measurement has 4 possible outcomes (the 4 Bell states). To communicate which one of the 4 possibilities occurred, you need 2 classical bits to get 4 possible combinations: 00,01,10,11.
					- Each Bell state gets assigned one of these 2-bit labels.
	- Protocol:
		- The protocol uses 3 qubits as specified below:
			- <img width="372" height="212" alt="image" src="https://github.com/user-attachments/assets/fb368713-a260-4b8d-b5f1-1db7b8825f15" />
			
			- A has 2 qubits, B has 1 qubit
			- A's quantum message (key) is $\ket{v}$ = $\begin{pmatrix} {a} \ & {b} \end{pmatrix}$ = a $\ket{0}$ + b $\ket{1}$
			- The entanglement between A's second qubit and B's qubit is $\frac{1}{\sqrt2}$ $\ket{00}$ + $\frac{1}{\sqrt2}$ $\ket{11}$
			- So, the quantum state of the 3 qubits is: (a $\ket{0}$ + b $\ket{1}$ ) ( $\frac{1}{\sqrt2}$ ket{00}$ + $\frac{1}{\sqrt2}$ $\ket{11}$ ) = $\frac{1}{\sqrt2}$ (a $\ket{000}$ + a $\ket{011}$ + b $\ket{100}$ + b $\ket{111}$ )
		- CNOT operator by A:
			- A applies CNOT gate to her qubits where q[2] is the control qubit and q[1] is the target qubit.
			- The new quantum state after this CNOT operator is: $\frac{1}{\sqrt2}$ (a $\ket{000}$ + a $\ket{011}$ + b $\ket{110}$ + b $\ket{101}$ )
		- A applies Hadamard gate to q[2] (leftmost in each state):
		-
	- Measurement by A:
		- A measures her qubits. With probability $\frac{1}{4}$ , she can observe one of the basis states.
		- Depending on the measurement outcomes, B's qubit is in the following states (same concept as above, the corresponding state is the term beside the respective states):
			- "00": $\ket{v_{00}}$ = a $\ket{0}$ + b $\ket{1}$
			- "01": $\ket{v_{01}}$ = a $\ket{1}$ + b $\ket{0}$
			- "10": $\ket{v_{10}}$ = a $\ket{0}$ - b $\ket{1}$
			- "11": $\ket{v_{11}}$ = a $\ket{1}$ - b $\ket{0}$
- **Multiple Control Constructions**:
	- How can we obtain the following operator, in which the NOT operator is applied to the target qubit if the control qubit is in **state $\ket{0}$ instead?**
		- <img width="502" height="226" alt="image" src="https://github.com/user-attachments/assets/67c9a035-68cc-475b-8daa-47a3a8afae1c" />
		
	- To do so, we can **apply a NOT operator** to the control qubit, then **apply CNOT operator** so that the NOT operator is applied to the target qubit when the control qubit has been in state $\ket{0}$ . To recover the previous value of the control qubit, we **apply the NOT operator once more** after the CNOT operator.
	- CCNOT:
		- Now we introduce **CCNOT gate**: controlled-controlled-not operator (Toffoli gate), which is controlled by 2 qubits (i.e 2 control qubits, 1 target qubit)
		- <img width="1180" height="524" alt="image" src="https://github.com/user-attachments/assets/3fefcde2-a798-42ec-a480-d7185772b2c0" />
		
- **Inversion about the Mean**:
	- We play a game to understand how Grover's search algorithm works:
		- We have a list of N elements. Some of them are marked. At the beginning, each has a value of 1. Each iteration of the game has 2 phases:
			- **Query**: We assume that each marked element is detected, and then its sign is flipped.
				-
				  ```def
				  def query(elements=[1], marked_elements=[0]):
				    for i in marked_elements:
				          elements[i] = elements[i] * -1
				  
				      return elements
				  ```
			- **Inversion**: The value of each element is reflected over the mean of all values.
				-
				  ```def
				  def inversion(elements=[1]):
				    sum = 0
				    for i in range(len(elements)):
				          sum += elements[i]
				    mean = sum / len(elements)
				    for i in range(len(elements)):
				          value = elements[i]
				          new_value = mean -(value-mean)
				          elements[i] = new_value
				  
				      return elements
				  ```
		- We iterate the same game X steps, where N = __ and the marked elements are the ___ elements. Print the length of the list of elements (i.e consider it as a **vector**) after each query and inversion phases. (Note that the initial length is $\sqrt{\sum^{N}_{i=1}{1²}}$ = $\sqrt{N}$ )
			- The reason why the length is $\sqrt{N}$ and not just N is because we **aren't just measuring the number of elements in the list** --- we are measuring the **geometric length of the state vector** in a quantum algorithm.
			- Since we are representing the state of the system as a vector, the system is in a **uniform superposition**, meaning that it has an equal probability of being in any of the N possible states. We are essentially assigning an amplitude to each element, i.e 1. Thus, our initial state vector will look like: $v$ = $\begin {bmatrix} {1} \ & 1 \ & 1 \ & . \ & . \ & . \ & 1 \end {bmatrix}$ (with N elements)
			- To find the length of vector $v$ , we use the standard Euclidean distance formula (Square each component, sum them up then take the square root of the total), which will give us $\sqrt{N}$
		- As observed, each phase is a **length-preserving operator**.
		- Now, we modify this game by guaranteeing that the list **represents a quantum state**.
			- If N = 8, what are the initial values for this new game?
				- The list is [a,a,a,a,a,a,a,a] at the beginning.
				- If it is a quantum state, then **its length must be 1**: 8a² = 1 → a = $\frac{1}{2\sqrt2}$
				- In general, any list with N elements is [ $\frac{1}{\sqrt{N}}$ , ... , $\frac{1}{\sqrt{N}}$ ]
				-
	- **Grover's quantum search algorithm**:
		- The modified game is the main part of Grover's quantum search algorithm.
		- Suppose that we are given an unordered list and we make a search of a specific element called **marked**.
			- We access the list via an oracle: we can make queries to the list
			- If there are N elements in the list, we use log(N) qubits (Assume that N is a power of 2).
			- Each basis state, i.e $\ket{0...0}$ , ... , $\ket{1...1}$ , correspond to an index of the list.
			- If the searched element is detected, then the oracle flips the sign of the corresponding **amplitude**.
			- Note that in the above games, we simulate the oracle with the pre-knowledge of marked element(s). In real implementations, the oracle should have a quantum mechanism detecting the marked elements while being in a **superposition of all indices**, then the sign(s) of the corresponding amplitudes(s) are flipped automatically → this is the main technological challenge for implementing Grover's search algorithm.
		- At the beginning, Hadamard operator is applied to each qubit. Thus, the amplitude of each basis state is set to $\frac{1}{\sqrt{N}}$
			- We can interpret this as all elements start the game with the same amplitude.
			- The game starts to iterate, and the amplitudes of marked and unmarked elements are changed.
		- The number of iterations:
			- When the number of marked elements are **less than** the unmarked elements, the **amplitudes of marked elements start to increase.**
			- Why is this the case?
				- We need to first understand that if there are fewer marked elements than unmarked elements, then when the oracle **queries** and **inverts** about the mean, the mean of all the amplitudes remains positive and relatively high BECAUSE there are only a few marked (negative) elements.
				- As for why the amplitudes start to increase, the new amplitude (new_value in the code for inversion) = 2 $\mu$ - $A_i$ , where $\mu$ = mean and $A_i$ = amplitude. Since $A_i$ is negative for the marked elements, the new amplitude is actually greater (minus a negative number)!
			- Then, we reach the first peak such that the probability of observing a marked element takes its maximum value.
				- We reach a peak because every iteration causes the marked element's amplitude to get bigger and bigger, which eventually starts pulling the mean $\mu$ down.
			- After passing this point, the amplitudes of marked elements start to decrease.
				- Past the peak, the amplitudes start to decrease as the mean becomes low enough that the inversion step begins to **shrink** the marked element's amplitude and push it back down.
		- Phases:
			- The operator in each phase is unitary (linear).
			- The unitary matrix in the query phase depends on the input, but the unitary operator in the inversion phase does not depend on the input.
			- In the query phase, the amplitudes of the marked elements change sign.
			- In the inversion phase, for each amplitude $x$ , the new value is calculated as mean - ( $x$ - mean) = 2mean - $x$ .
			- The mean of a column vector of size N can be calculated by multiplying it with the row vector from the left: $\begin{pmatrix} \frac{1}{N} & \frac{1}{N} & \dots & \frac{1}{N}\end{pmatrix}$
			- When considering all elements in the list, we work with a matrix. The matrix for the second phase should be: D = 2 $\begin{pmatrix} \frac{1}{N} & \dots & \frac{1}{N} \\ \vdots & \ddots & \vdots \\ \frac{1}{N} & \dots & \frac{1}{N}\end{pmatrix}$ - $I$
			- To prove: D $\begin{pmatrix} {x_1} \\ \vdots \ & {x_N} \end{pmatrix}$ = $\begin{pmatrix} {2m - x_1} \\ \vdots \ & {2m - x_N} \end{pmatrix}$ , where $m$ = $\frac{\sum_{i=1}^{N}{x_i}}{N}$
				- [2 $\begin{pmatrix} \frac{1}{N} & \dots & \frac{1}{N} \\ \vdots & \ddots & \vdots \\ \frac{1}{N} & \dots & \frac{1}{N}\end{pmatrix}$ - $I$ ] ( $\begin{pmatrix} {x_1} \\ \vdots \ & {x_N} \end{pmatrix}$ ) 
				    
				  = 2 $\begin{pmatrix} \frac{1}{N} & \dots & \frac{1}{N} \\ \vdots & \ddots & \vdots \\ \frac{1}{N} & \dots & \frac{1}{N}\end{pmatrix}$ $\begin{pmatrix} {x_1} \\ \vdots \ & {x_N} \end{pmatrix}$ - $\begin{pmatrix} {x_1} \\ \vdots \ & {x_N} \end{pmatrix}$  
				    
				  = [ $\begin{pmatrix} 2(\frac{x_1}{N} + \dots + \frac{x_N}{N}) \\ \vdots \ & 2(\frac{x_1}{N} + \dots + \frac{x_N}{N})\end{pmatrix}$ ]  
				    
				  = $\begin{pmatrix} {2m - x_1} \\ \vdots \ & {2m - x_N} \end{pmatrix}$ , where $m$ = $\frac{x_1 + \dots + x_N}{N}$ = $\frac{\sum_{i=1}^{N}{x_i}}{N}$  
				-
			- Let A = $\begin{pmatrix} \frac{1}{N} & \dots & \frac{1}{N} \\ \vdots & \ddots & \vdots \\ \frac{1}{N} & \dots & \frac{1}{N}\end{pmatrix}$ . Convince yourself that A² = A (A is **idempotent**) and $D^T$ = D.
				- To prove that A is idempotent (square matrix where A² = A):
					- We know that the entry in the $i$ -th row and $j$ -th column is the dot product of the $i$ -th row of A and $j$ -th column of A:
					    
					  $(A²)_{ij}$ = $\sum^{N}_{k=1}{A_{ik}}{A_{kj}}$  
					    
					  Since every single entry in A = $\frac{1}{N}$ , we can substitute $A_{ik}$ = $A_{kj}$ = $\frac{1}{N}$  
					    
					  $(A²)_{ij}$ = $\sum^{N}_{k=1}{\frac{1}{N²}}$ = N ⋅ $\frac{1}{N^2}$ = $\frac{1}{N}$  
					    
					  Every entry of the resulting matrix $A^2$ simplifies to $\frac{1}{N}$ , thus $A^2$ = A (shown).  
					-
				- To prove that $D^T$ = D, i.e the transpose of D = D:
					- D = $\begin{pmatrix} \frac{2}{N} & \dots & \frac{2}{N} \\ \vdots & \ddots & \vdots \\ \frac{2}{N} & \dots & \frac{2}{N}\end{pmatrix}$ - $I$
					    
					  Tranpose of the identity matrix $I$ equals itself.  
					    
					  Since every entry in $\begin{pmatrix} \frac{2}{N} & \dots & \frac{2}{N} \\ \vdots & \ddots & \vdots \\ \frac{2}{N} & \dots & \frac{2}{N}\end{pmatrix}$ is equal to $\frac{2}{N}$ , the transpose of this matrix is also equal to itself.  
					    
					  Thus, the transpose of D (which is made up of the matrix and the identity matrix only) is equal to D (shown).  
					-
				- Lastly, prove that $D$ is unitary by showing that $D^T$ ⋅ $D$ = $I$ , knowing that $D$ = $2A - I$
					- $D^T$ ⋅ $D$ = ( $2A - I$ ) $^2$
					    
					  = 4 $A^2$ - $4AI$ + $I^2$  
					    
					  = $4A$ - $4A$ + $I$  
					    
					  = $I$ (shown)  
	- **General form of Grover's search algorithm**:
		- Assume that there are $N = 2^N$ elements in a list L, and one of the elements is marked.
		- Suppose there exists a function $f$ whose domain is L with the following properties:
			- $f(x)$ = 1      if $x$ is marked
			- $f(x)$ = 0     otherwise
			-
		- Grover's algorithm can also be defined in a more general form: for the given function $f$ , it finds the element $x$ such that $f(x)$ = 1.
		- We access the list by querying $f$ (called the oracle). In the worse case scenario, you would have to query $f$ for all possible inputs to find $x$ satisfying $f(x) = 1$ which has query complexity O(N).
		- Grover's algorithm is able to perform the same task only with O( $\sqrt{N}$ ) queries.
	- Example:
		- Grover's algorithm is not restricted to a list. It can be applied to any **search space** as long as a function $f$ can be constructed. <img width="646" height="434" alt="image" src="https://github.com/user-attachments/assets/dea9f135-43be-48f0-a247-f52b6dad3c38" />
		
		- Consider the Travelling Salesman Problem above. In this example, the search space consists of all possible routes such as ABDCA, ACBDA, ABCDA etc., and our aim is to find the route whose total distance is <900.
			- ABCDA fulfills this condition. If you want to design $f$ for this problem, $f(ABCDA)$ = 1 and $f(x)$ = 0 for all other routes.
			- Checking all routes one by one is a long procedure. But given a route, you can easily check if the total distance satisfies the condition. Instead of checking all routes one by one and querying $f$ for each route, it is enough to make square root queries if you use Grover's Search.
