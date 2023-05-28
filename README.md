# MiniCase1
Whiskas Case Team 4
Instructions
Please follow the instructions below to complete the assignment:

Read the Whiskas case description provided.

Run the provided code snippets, WhiskasModel1 and WhiskasModel2, related to the Whiskas problem.


!pip install pulp
Looking in indexes: https:/Lpypi.org/simple, https://us-python.pkg.dev /colab-wheels/public/simple/
Collecting pulp
Downloading PuLP-2.7.0-py3-none-any.whl (14.3 MB)
14.3/14.3 MB 42.9 MB/s eta 0:00:00
Installing collected packages: pulp
Successfully installed pulp-2.7.0
0 s
• # Import PuLP modeler functions from pulp import *
# Create the 'prob' variable to contain the problem data
prob = LpProblem "The Whiskas Problem", LpMinimize)
# The 2 variables Beef and Chicken are created with a lower limit of zero
×1 = LpVariable("ChickenPercent", 0, None, [pInteger)
×2 = LpVariable("BeefPercent", 0)
# The objective function is added to 'prob' first
prob += 0.013 * x1 + 0.008 * ×2, "Total Cost of Ingredients per can"
# The five constraints are entered
prob += x1 + ×2 == 100, "PercentagesSum" prob += 0.100 * ×1 + 0.200 * ×2 >= 8.0,
"ProteinRequirement"
prob += 0.080 * ×1 + 0.100 * ×2 >= 6.0,
"FatRequirement"
prob += 0.001 * x1 + 0.005 * ×2 <= 2.0,
"FibreRequirement"
prob += 0.002 * x1 + 0.005 * x2 <= 0.4,
"SaltRequirement"

# The problem data is written to an Ip file
prob.writeLP( "WhiskasModel.lp")
# The problem is solved using PuLP's choice of Solver
prob.solve ( )
# The status of the solution is printed to the screen
print ("Status:", LpStatus [prob.status ])
# Each of the variables is printed with it's resolved optimum value
for v in prob.variables ( ):
print (v. name,
11 _ 11 v.varValue)
# The optimised objective function value is printed to the screen
print ("Total Cost of Ingredients per can =
", value (prob.objective))
[› Status: Optimal
BeefPercent = 66.0
ChickenPercent = 34.0
Total Cost of Ingredients per can = 0.97
/usr/local/lib/python3.10/dist-packages/pulp/pulp.py:1352: UserWarning: Spaces are not permitted in the name. Converted to ' warnings.warn("Spaces are not permitted in the name. Converted to ' '") 
