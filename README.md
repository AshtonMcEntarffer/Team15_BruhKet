# Team15_BruhKet

## Phase 1: Reading and Planning

First we started reading through the documentation. We wanted to understand what exactly we would be submitting, how we would be judged, and what exactly our goal was to accomplish.
We determined that our foremost goal was to find which model had the highest accuracy

To go about our project, we first decided to go through all of the relevant documentation and information to ensure that we had a good understanding of exactly what it was that we were trying to accomplish, and how exactly we might best be able to do that. We read through the SCQ_IonQ_Challenge notebook as well as the Ansatz library and the Optimization notebook. As we did so we researched any terms we didn’t know so that we understood everything we were working with.
After going through the documentation, we decided that the primary way to create the model with the highest accuracy was to identify the main variables that differentiate each pipeline, identify which variables would be most likely to have the highest performance for binary visual classification, and test the different combinations.

We noticed that the time it took to train some models was significant, so we researched how we might optimize our models
the transiple method doesn’t appear to be the best optimizer
Time seems to be mostly affected by the type of ansatz, and the number of qubits and other parameters. More qubits means you should use less parameters, and vice versa.

## Phase 2: Model Analysis

We decided that the best approach would be to first try and find the best relative performance of different combinations of ansatz, encoder types.
We kept the amount of qubits and gates and epochs low
4 qubits
5 cnot (2 qubit) gates | entanglement depth = 2
6 epochs
In order from greatest to least, we think the following ansatz will provide the best accuracy: ***GO BACK AND JUSTIFY SOME MORE
QCNNAnsatz (Most likely to give high accuracy due to its design for image-like data)
BrickworkLayoutAnsatz
AngleEncoder
QAOAAnsatz
ButterflyOrthogonalAnsatz
CrossOrthogonalAnsatz
UnaryEncoder (Least likely to give high accuracy for this specific task)
In order from greatest to least, we think the following encoder types will provide the best accuracy: ***GO BACK AND JUSTIFY
amplitude
qubit
angle
fourier
iqp
basis
unary
To analyze the ansatz, we use only angle data, as that is fairly accurate and also fast, so that we can see which ansatz perform better in a reasonable amount of time
To analyze the encoder type, we use only the QAOAAnsatz, as this seems to be fairly accurate and also fast, so that we can see which encoder type performs better in a reasonable amount of time
For analysis, we use this Pauli:
SparsePauliOp(["IIIX"]) 
SparsePauliOp(["IIXI"]) 
SparsePauliOp(["IXII"])
SparsePauliOp(["XIII"])

After analyzing the various ansatz it appears that the QCNN and Brickwork architectures worked the best. We are now going to analyze those two ansatz with various subparameters to maximize their accuracy with the angle encoder, as that is the only preset that appears to be working properly right now. Ashton is working on creating custom encoders as well.
After we analyze the optimal parameters and encoder types, we are going to find the best combination. If we have time we will try to create custom ansatz and encoders based on our findings to see if we can increase accuracy any further.
Lastly, we will compile our findings and create our presentation.

It appears that the only worthwhile custom encoder to pursue would be the amplitude encoder, but this would only be possible with a custom ansatz, so we will pursue that after our benchmark of the provided ansatz.
We tried building amplitude, qubit, fourier, iqp, basis, and unary encoders but there is an error in the framework, so we can’t pursue these right now. We are using the angle encoder to find the most optimal subparameters for the QCNN and Brickwork ansatz for accuracy.

Summarizing our results for Pauli List:
For Brickwork ansatz we found that the most optimal accuracy occurred at a Pauli list of SparsePauliOp(["IIIX"]), SparsePauliOp(["IIXI"]), SparsePauliOp(["IXII"]), SparsePauliOp(["XIII"])
For the QCNN we found that the most optimal accuracy occurred at a Pauli list of X0,Y0, Z0, X2
Summarizing our results for Entanglement:
For the Brickwork ansatz we found that optimal accuracy occurred at 4, having tested 3, 4, 5
For the QCNN accuracy peaked at…
Summarizing our results for Qubits:
For the Brickwork ansatz we found that 4 was the most optimal number of qubits for accuracy and time
For the QCNN we found that 4 qubits was the most optimal number in terms of accuracy and time
