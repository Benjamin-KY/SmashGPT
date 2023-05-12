Adversarial testing involves crafting adversarial examples — inputs that are designed to cause the model to make mistakes. There are several methods to do this, each with its own strengths and weaknesses:

1. **Fast Gradient Sign Method (FGSM):** This is a simple and effective method for generating adversarial examples. It works by using the gradients of the neural network to create perturbations that maximize the loss function. This method is computationally efficient but may not always produce the most effective adversarial examples.

2. **Basic Iterative Method (BIM):** This is an extension of FGSM which applies the FGSM multiple times with small step size and clips pixel value of intermediate results after each step to ensure that they are in an epsilon neighborhood of the original image. It generally produces more effective adversarial examples than FGSM.

3. **Projected Gradient Descent (PGD):** This is a more sophisticated method that performs a random start followed by a specified number of FGSM steps. PGD is more computationally expensive than FGSM, but it tends to produce more effective adversarial examples.

4. **Jacobians-based Saliency Map Attack (JSMA):** This is a method that uses the forward derivative (Jacobians) of the model to identify the most sensitive pixels to perturb. It is less likely to be detected compared to the others since it only modifies a small subset of the input features, but it is computationally expensive.

5. **Carlini & Wagner (C&W) Attack:** This method minimizes a different objective function than the others that considers both the perturbation and the confidence of misclassification. It tends to produce high-quality adversarial examples, but it is the most computationally expensive among these methods.

6. **DeepFool:** This method iteratively computes the minimal perturbation that can change the model's output. It approximates the decision boundary to be linear in each step and moves the sample across the boundary along this direction. It tends to produce less perceptible adversarial examples.

In practice, it's often beneficial to use a combination of these methods to test a model's robustness to adversarial attacks. It's also important to consider the model's application when choosing a method. For example, if the model is used for image recognition, you might prioritize methods that produce less perceptible adversarial examples.

Note that while these methods are helpful for testing machine learning models, they can also be used by attackers. Therefore, it's important to also consider defenses against these attacks, such as adversarial training, defensive distillation, feature squeezing, or robust optimization methods, among others.