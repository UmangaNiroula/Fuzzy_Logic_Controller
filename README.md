# Fuzzy_Logic_Controller

1.	Introduction
   
1.1.	Project Overview
The main goal of this project is to create a system for the disable residence, that can control the equipment’s such as heater, light, and fan automatically based on the environmental parameters such as temperature, lights and humidity. Further, this smart home control system needs to be created using the Fuzzy Logic Controller (FLC). This report will discuss about the design, optimize, and evaluate phase of the FLC. Three parts are explain in this section; designing the FLC, optimizing the FLC by using Genetic Algorithm (GA), and comparison of optimizing techniques such as Particle Swarm Optimization (PSO) and Differential Evolution (DE) on benchmark functions.

1.2.	Problem Statement
Instead of traditional control system which heavily relies on mathematical expression, that requires human innervation to control various devices. As a result, such systems aren’t the optimum solution for disable individuals. Further, there is a need of an intelligent system that can automate parameters based on the real-time sensor inputs such as temperature, light, and humidity. Hence, a consideration of FLC system, which automates these parameters based on the membership functions of input sensors, is done in this project known as smart house control system. However, manually controlling the parameters and fine-tunning the FLC can be very complex and time consuming. Therefore, a requirement of optimization for the FLC system is also required along with evaluation that can provide insight into the performance of the system based on real-life sensor data (Khalid et al., 2019). 

1.3.	Objectives
The objective of this section of the reports are to:
•	Design a FLC for disable individual in context of controlling house appliance such as heater, light, and fan automatically.
•	Optimize the FLC system through the utilization of Genetic Algorithm.
•	Comparison of Optimization techniques (PSO and DE) on two benchmark functions. 

2.	Part 1: Fuzzy Logic Controller Design
   
2.1.	Overview and Importance of FLC 
FLC nowadays has gained tons of attraction for areas such as smart home systems. They make the automation process very easy and swift. In the context of this report, the FLC has made it easy to automate parameters such as temperature, light, and fan. The reason for this popularity is that, the FLC system does not rely on exact formulas that other control systems would have been based on. Further, this system acts more or less like humans, the decision-making process based on experience even during unclear situations is something that makes the FLC system close to human-made decisions. As a result, this makes FLC the perfect choice for smart homes, where various external parameters such as temperature humidity, and light can change suddenly (Zhang, Sathishkumar & Samuel, 2020). For example, instead of turning the heater or fan on or off, FLC can adjust the level of heat of speed of fan based on the increase or decrease of temperature, reducing excessive energy consumption and ensuring optimum comfort. (Alowaidi, 2022).

2.2.	Selection of Fuzzy Inference Model
For this report, the Mamdani fuzzy inference model is chosen. This model was considered due to its simplicity and the ability to mimic human-made decisions based on the conversion of inputs into outputs by utilizing the set of “if-then” fuzzy rules. The following figure illustrates the working principle of the Mamdani model where a crips input, for instance, a temperature of 30 degree Celsius can be considered. The crisp value is then converted into fuzzy values by mapping it into various ranges of membership functions which are either low, medium, or high. Following the fuzzy value, fuzzy rules are implemented where the inference engine processes trhough fuzzy logic and provide a fuzzy output that needs to be defuzzified to obtain a crips value. For example, if the output of the fan suggests medium speed based on the input parameters, then this value can be defuzzified into a crisp value of 55% of fan speed (Ahmadi et al. 2020).

![Picture1](https://github.com/user-attachments/assets/2e206b35-d36f-4119-85fd-c5bac495d731)

Figure 1: Working Principle of Mamdani Fuzzy Inference Model (Ahmadi et al. 2020).

Likewise, other models, such as Sugeno fuzzy models are also in common use which heavily relies on more mathematically driven approach. Implementing this model would shift the process into obtaining more precise output based on mathematically expressions. As a result of this implementation, the defuzzification process will be simplified as the fuzzy sets will be replaced by crisp functions. Hence, instead of obtaining a fuzzy output such as high, low, or medium, which requires to be defuzzified, the Sugeno model directly converts the output into a crisp value which is a precise numerical value. While the system’s efficiency may rise in comparison to Mamdani model, implementation of Sugeno will eliminate the user-friendly approach, as fuzzy outputs are easy to understand by humans rather than the mathematical approach. Overall, in the context of smart home applications where transparency is a top priority, the Mamdani model has a higher advantage of easy interpretability in comparison to Sugeno model (Mudia, 2020).

2.3.	Input/Output Fuzzy Sets and Membership Functions Design
Following are the inputs, outputs, and membership function considered for the smart home control system using FLC:

Inputs include:
•	Temperature (°C)
•	Light (lumens)
•	Humidity (%)

Outputs include:
•	Heater output (%)
•	Light brightness (%)
•	Fan speed (%)

Fuzzy sets include:
•	Temperature fuzzy sets:
Here, the utilization of Gaussian function is used as it provide smooth transaction between categories like cold, warm, and hot. This membership function is ideal for temperature as this parameter has frequent changes in its value. As a result, the Gaussian function provides a realistic overlap in the fuzzy logic as a temperature of 15 degree celsius can both be considered warm and cold according to various scenarios (Lam, 2018). 

![Picture2](https://github.com/user-attachments/assets/4bd3e50e-ca53-45fa-82ff-3f5fb6693af1)

Figure 2: Temperature Fuzzy Sets.

As shown in the above figure, which illustrates the gaussian function for temperature by dividing its value into three categories: cold, warm, and hot. The blue curve represents cold which is a temperature around 0-15°C. Likewise, the orange curve shows the represents warm temperature, that peaks at 20°C, while the green represents hot temperature of value 25°C to 40°C.

•	Light fuzzy sets:
Trapezoidal function are used for the light, as it created a wide, flat are in the middle, meaning that when the light level reaches a certain level then it stays the same even with slight changes to the external parameter. For, example if the light is dim, the it will stay dim even with changes occurring in the external parameter. This helps to avoid the sudden change in light categories such as dim, moderate, and bright, making the system more stable and less sensitive to change (Ali et al., 2015).

![Picture3](https://github.com/user-attachments/assets/587efdc9-c180-47b0-b6b5-8ddeac93a40a)

Figure 3: Light Fuzzy Sets.

The above figure presents the trapezoidal function for light categories, which consists of dim, represented by blue line which decreases as the light increases, moderate, represented by orange line which peaks at 40 and 60, and finally bright, represented by green line which increases as the light value gets higher.

•	Humidity fuzzy sets:
For humidity, again trapezoidal function is used as similar to light for the same reason, as this function creates a wide flat area in between which is stable for even slight changes in the external parameter. 

![Picture4](https://github.com/user-attachments/assets/b7afcfc1-0dbc-483d-90a4-2a13dd948e54)

Figure 4: Humidity Fuzzy Sets.

Similar to the light fuzzy set diagram, this also has the same graph where the blue line represents low humidity that covers from 0 to 40%. Likewise, the orange line represents medium humidity that peaks around 50%, and finally the green line represents high humidity covering form 60% which increases further.

•	Heater, light, and fan output sets: 
For the output fuzzy sets, like heater, light, and fan Triangular functions is used as they are simple and faster for the system to compute. For, each of the outputs three categories have been identified which is "low," "medium," and "high." With the help of this function the transition process is smooth out, for example if the fan speed is moving from "low" to "medium" then, with the help of this function the transition is simple and effective without the need of complicated calculation (Ali et al., 2015). 
 
![Picture5](https://github.com/user-attachments/assets/97f93b42-ccfa-48f7-93ba-606558614fd7)

Figure 5: Heater Fuzzy Sets.

![Picture6](https://github.com/user-attachments/assets/65d1b50b-5dcb-42ab-8258-04d21143c99c)

Figure 6: Light Output Fuzzy Sets.

![Picture7](https://github.com/user-attachments/assets/4974a643-ae79-44eb-b2b9-8a3a45b60ccc)

Figure 7: Fan Fuzzy Sets.

2.4.	Rule Base Development
For the rule base development, a set of ten rules were considered which is shown by the following figure. The rule base is collection of “if-then” statement, defining the relation of system to various input parameters (Afroz et al., 2018). Some of the examples of the system is mentioned below:
•	If temperature is cold and light is dim, then set heater at high and light output at bright. 
•	If temperature is hot and humidity is high, then set the fan at high.
•	If the temperature is warm and light is moderate, then set the heater at
•	If the temperature is hot and light is bright, set the light output at dim.

Further, following figures shows the entire rules defined by the system.

![Picture8](https://github.com/user-attachments/assets/5ce7c019-f3f7-425f-aeee-5f601499188f)

Figure 8: Defining Fuzzy Rules.

2.5.	Defuzzification Method
As discussed early the inference engine produces fuzzy output based on the rule described. Once the fuzzy output is obtained, for it to be used to control the output devices such as heater, light output, and fan the fuzzy output should be converted into a crisp value. Further, this process of converting fuzzy output to crisp value is known to be defuzzification. For the defuzzification process, Centroid method is used which calculates the average between the strong and least likely suggestions. Meaning, when the fuzzy logic gives output, it doesn't give a specific answer, rather it provide various range of answer each with its own impotance level. For example, the fuzzy output might say the fan's speed could be set to low and medium with low having higher importance. Further, with such suggestion the Centroid method calculates the center point of the fuzzy set by giving more importance to the stronger suggestions (Sharma et al., 2014). 

2.6.	System Behavior Analysis

2.6.1.	Test Scenarios and Simulation Results
To evaluate the FLC system, five test scenario were built, each of the test scenario has various input value ranging from high to low values:

Scenario  Temperature	    Light	      Humidity	  Heater	    Light	    Fan

1	          5°C	          20 lumens	   30%	      81.4%	     81.4%	    50%

2	          22°C	          50 lumens	   60%	      50%	     50%	       47.3%

3	          35°C	          80 lumens	   90%	      No Output  19%	       80%

4	          8°C	          90 lumens	   20%	      83.2%	     25%	       75%

5	          25°C	          10 lumens	   80%	      75.1%	     75.1%	    50%

From the above table we can observer that when the temperature is low (5°C and 8°C) the heater output is high. Likewise, if the temperature is at moderate (22°C and 25°C) then the heater output stays at around 50-75%. Finally, if the temperature reaches higher values (35°C), there is no heater output as heating is unnecessary. Further, for the lower light input values (10-20 lumens) the light output is high and opposite for the higher light input values (80-90 lumens). Similarly, the FLC system seems to perfectly maintain the fan output based on temperature and humidity, for example when temperature is 35°C and humidity is at 90% the fan output is at 80%. Overall, with various test scenario, it is prominent that the system responds well to environmental change.

2.6.2.	Control Surface Analysis
To further visualize the understanding of the FLC, three graphs were created between temperature and light to visualize the heater output. Likewise, the relation between temperature and humidity against fan out was also created, and family the light output vs. light input was also shown in graph (Zhang, Sathishkumar & Samuel, 2020). The following graph shows, the role of temperature and light to control the heater output. As illustrated by the graph and the above test scenario that when the light and temperature values are low then the heater output is high and vice versa when the light and temperature values are high.  

![Picture9](https://github.com/user-attachments/assets/b9648d74-a1a9-4d0a-a305-089544d4f6d8)

Figure 9: Heater Control Surface: Temperature vs Light Input.

Similarly, the following 3D plot surface graph shows the visualization between temperature and humidity to control the fan output. As shown in the graph, the fan output value increases with the increase in temperature and humidity levels and vice versa for the lower levels. Further, there are dip and rise in fan output based on various combinations of temperature and humidity. 

![Picture10](https://github.com/user-attachments/assets/5590247d-7fa1-4911-98aa-f7ba4ae282de)

Figure 10: Fan Control Surface: Temperature vs Humidity.

Finally, the following line graph shows the relation between light input and output. Similar, to the explanation done in the test scenario with lower light input, the output is high and vice versa for the lower input light level, where at around 80 lumens and beyond, the output stabilizes at a low level.


![Picture11](https://github.com/user-attachments/assets/8de7c4ed-6139-4969-b50e-83c55474cd7f)

Figure 11: Light Control Response: Light Input vs Light Output. 

3.	Part 2: Genetic Algorithm Optimization of FLC
   
3.1.	Overview of Genetic Algorithm (GA) Optimization
For the tuning process of the FLC system, this project will demonstrate the use-age of Genetic Algorithm (GA), which is a wide known optimizing method inspired by natural evolution process. This method is especially used in scenarios where the tuning process is highly complex manually. Hence, in this project, the GA method is used to fine tune the environmental elements (temperature, light, and humidity) automatically. This method involves creating a random set of solutions, picking the best solution based on fitness score, combining all the selected solution to create more advanced solution, exploring new possibility by tweaking small change to the same solution to maintain diversity, and finally repeating this process until an optimum solution is obtained. Hence, with the implementation of this method there is no need for tweaking changes in the FLC in order to optimize the output, the method itself will handle the tweaking process with various trial (Lambora, Gupta and Chopra, 2019).

3.2.	Chromosome Encoding for FLC Optimization
As described earlier, the principle in which the GA works is to find the best possible solutions through various selection, crossover, mutation, and repeating the same process. Hence, the core of GA lies on finding the best possible solution. Further, possible solutions are also known to be "chromosomes", and each set of chromosomes represents various changes for the FLC. For each of the membership function and rules applied, genes are used to control them. Genes are basically a collection that forms chromosomes. For example, in triangular membership function, the genes help to decide the position for triangle's point, where as in Gaussian they control the center and width of the curve. With the help of these genes, the GA method check how the FLC responds to various scenarios. For example, the genes constantly change the value of medium temperature for testing purpose. With this change the GA notices how the FLC responds either to turn up the heat or low it down. Hence, based on the output obtained, the method identifies the best configuration that optimizes the FLC (Pelusi, 2011).

3.3.	Fitness Function Definition
The fitness function is the key evaluation portion of Genetic Algorithm (GA), which evaluates how each of the chromosomes makes the FLC output to behave as the expected. In short, the function checks how well the tuning done to FLC, makes the home for disable individuals comfortable through controlling each of the devices (heater, fan, and light output) with high accuracy. Further, fitness function with a lower value translates to a better solution as it shows that the FLC is giving as expected output. The measurement for the fitness function is done through calculation of um of squared errors (SSE), which the GA tries to reduce. The SSE measures how much the FLC output difference from the targeted output. For instance, the following table shows the SSE for temperature which was reduced from 187.64 to 83.70 in lower temperature ranges (Costa et al., 2023).

3.4.	Results of Optimization
As explain above, the GA optimizes various control factors of FLC which are listed below:

•	Heater Control: The following table shows the SSE for heater before and after the use of GA methods, as a result it is safe to conclude that the Gaussian membership function used in the temperature to predict the heater output was highly effective in reducing the error. 

Inputs (Temp, Light, Humidity)	Initial Error (Heater)	Optimized Error (Heater)
      
       (55, 70, 130)	                   0.54	                   0.19
       
       (50, 65, 120)	                   12.72	                1.43
       
       (55, 70, 130)	                   0.54	                   0.19

•	Light Control: The following table shows the SEE for light output before and after the use of GA methods on FLC. Hence, it is safe to conclude that the trapezoidal membership function used has optimized the FLC to obtained expected outputs by reducing the error.

Inputs (Temp, Light, Humidity)	Initial Error (Light)	Optimized Error (Light)
        
        (5, 20, 30)	                    265.97	                96.31
        
        (50, 65, 120)	                  27.12	                4.79
        
        (55, 70, 130)	                  27.89	                4.47

•	Fan Speed Control: The following table shows the SSE values for the fan output before and after the use of GA method. Here, triangular membership function was used, which doesn’t have a huge effect on the decrement of the error, however it does slightly decrease the error but still improvements can be done.
Inputs (Temp, Light, Humidity)	Initial Error (Fan)	Optimized Error (Fan)

         (50, 65, 120)	                125.59	             118.79
         
         (50, 65, 120)	                117.97	             109.12
         
         (55, 70, 130)	                125.59	             118.79

3.5.	Membership Function Breakdown
The GA optimized several types of membership functions for the FLC:

Temperature (Gaussian MFs): The following graph shows the Gaussian membership function for temperature parameter which highlights the smooth change between cold, hot, and warm temperature.  In the following graph we can clearly see that as temperature value decreases, there is a sharp increase in cold value represented by blue line. Similarly, the warm temperature represented by orange lien increases as the temperature increases. Finally, the green line represented by hot temperature shows similar behavior to the warm temperature line, however the overlap shows the system can responds accurately with smooth transaction and without sudden shift (Belkadi, Mezghani and Mami, 2020).

![Picture12](https://github.com/user-attachments/assets/458e364e-0cdc-4525-8b40-9b21a724f0e5)


Light (Trapezoidal MFs): The following graph shows the membership function for light parameter which uses the trapezoidal membership function. As seen in the graph, there is a flat region for every line which the system has identified as fully dim, bright, or moderate. Also the gradual increase or decrease in each line creating a slope transition allows smoother change and avoiding sudden shift (Belkadi, Mezghani and Mami, 2020).

![Picture13](https://github.com/user-attachments/assets/20ce079a-9383-481d-83fc-31b9a6599b8b)
 
Humidity (Triangular MFs): The following graph represents the membership function for humidity which uses the triangular membership function, which provides a sharp increase or decrease between the humidity levels. Further, the peak in each of the levels suggests where the system is certain about the humidity type. Similarly, the between all three-humidity type shows the avoidance of sudden change and implementation of smooth transactions (Belkadi, Mezghani and Mami, 2020).
 
![Picture14](https://github.com/user-attachments/assets/44dfbb9e-5773-44fa-8e00-8dc531465323)

Heater Output (Triangular MFs): Similar to the humidity, membership function, heater also utilizes the triangular membership function where each of the peak shows by the lines represents the consideration of particular type of heater level. Likewise, the overlap between the lines shows smooth transition as the system would treat 60 control value as both medium and high which helps to avoid sudden change (Belkadi, Mezghani and Mami, 2020).

![Picture15](https://github.com/user-attachments/assets/e18099d8-f588-4b1c-9b01-04968af3e35d)

Light Output (Triangular MFs): The Light also utilizes the triangular membership function where each of the peak for different line means the system considers them to be of a specific type. Similarly, the overlap between the lines shows smooth transition and helps to avoid sudden change.

![Picture16](https://github.com/user-attachments/assets/345e3499-d5c0-4f2d-9eda-381ed5bd7d48)

Fan (Triangular MFs): The Fan again utilizes the same triangular membership function as humidity, heater, and light. As mentioned earlier each of the peak means the system considers them to be of a specific type. Similarly, the overlap between the lines helps to avoid sudden change and allow smooth change between the fan level.

![Picture17](https://github.com/user-attachments/assets/c379f6e3-1f1d-4414-8ad3-2e75e92e557b)

 
 
4.	Part 3: Comparative Analysis of PSO and DE 

4.1.	Overview of Optimization Techniques
In this section of the report, we will further dive into comparison of two popular optimization techniques: Particle Swarm Optimization (PSO) and Differential Evolution (DE). Similar to the GA method, both of them helps us find the best solution to optimize a task, like helping to find the quickest route to solving a maze. Unlike, GA which was used in the FLC system, here two CEC'2005 benchmark functions will use used. Further, the mean and stander deviation will be use to evaluate both the optimization techniques in Shifted Sphere Function and Shifted Rastrigin’s Function which are the benchmark functions. Following is a simple definition both the benchmark function:

•	F1 (Sphere): This is a simple function which can also be refereed to as unimodal  function. The unimodal functions are those that have only one particular solution. Hence, this is used to check how fast the algorithm can solve and find the best possible solution (Suganthan et al. 2005).

![Picture18](https://github.com/user-attachments/assets/1874e97d-ef6d-4260-a982-59940e86a4fe)


•	F9 ( Shifted Rastrigin): This problem is much tricky, as a result they are also refereed to as multimodal function. These functions have multiple options where one of them being the best possible situation. This test how well the algorithm can avoid not getting stuck in other solutions to find the best possible solution (Suganthan et al. 2005).

 ![Picture19](https://github.com/user-attachments/assets/9fc16ffa-46bb-4e54-9a97-ba09ff25d2f5) 

Moreover, the reason for the choice of both this benchmark function is as they both represent different type of challenges. The F1 helps to identify how fast the algorithm can find the best possible solution whereas F9 helps to identify how well the algorithm can tackle with various problems and still find the best possible solution (Tresnadi et al. 2021).

4.2.	Experiment Setup and Parameters
For the experimental setup, Particle Swarm Optimization (PSO) and Differential Evolution (DE) were used to solve the benchmark function of F1 and F9 explain above. In order for the optimization to solve the problem 30-dimensional space was mentioned, which can be visualized a huge filed that consists of tone of areas to look for the problem, meaning the with 30-dimensional space the area is huge making is more complicated to find the best algorithm. Also, in order for both the algorithm to find the best possible situations 100 iterations has been allocated, to find the best solution. In order to obtain better output, the iteration can be increased but as the iteration is increased the consumption of computational power is also increased. After the 100 tires is completed mean and standard deviation is used to evaluate the optimum algorithm. Further, explain into the evaluation method is mentioned below:

•	Mean: This is an average of all the solution found by the algorithms. A lower value is mean refers to better performance as it means that the algorithm found better solutions in an average.

•	Standard Deviation: This shows the change between the solution of one try to the another, a lower value refers to higher similarities between the solutions where as a higher value refers to a drastic change in two solutions.

Moreover, by looking at the average and the consistency of the solutions, the evaluation can be done on which algorithm out performed. (Suganthan et al. 2005)

4.3.	Performance Analysis and Discussion
After running the algorithm, following were the output for both the function:

•	F1 (Sphere Function):

Algorithm	     Mean	                    Standard Deviation (Std)

  PSO	           7537.611398528888	           1655.9970941347706
  
  DE	           6.852441419298838e-14	        9.583286059978823e-14

From the above, table it is prominent that DE out performed PSO, as the mean and standard deviation for PSO are high suggesting it wasn’t close to the ideal solution and the solutions varied by a drastic measure. Nonetheless, the DE was quite close to the optimum solution as the mean is very close to zero value and likewise the solutions were consistent.

•	F9 (Shifted Rastrigin Function): 

Algorithm	     Mean	                    Standard Deviation (Std)

  PSO	           8243.523835556705	           2702.96999554988
  
  DE	           99.16390584955525	           8.137266574246135

From the above, table DE has once again out performed PSO, as the mean and standard deviation for PSO are high suggesting it wasn’t close to the ideal solution and the solutions varied by a drastic measure. Nonetheless, the DE was quite close to the optimum solution but in comparison to PSO by a huge margin and likewise the solutions were consistent as the Std is lower. 

5.	Final Conclusion
Overall, this project demonstrated the implementation of FLC in smart home control system for the disable individuals, alongside optimizing the FLC models with GA optimization technique which had a positive change to the system. Likewise, other optimization techniques such as PSO and DE were also used in two benchmark functions to see evaluate their performance. 
