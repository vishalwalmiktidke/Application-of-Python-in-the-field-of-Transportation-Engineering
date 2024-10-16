# Application-of-Python-in-the-field-of-Transportation-Engineering
ASSIGNMENT NO. 03


Q.1) # To Calculate the length of transition curve
v = int(input("Enter the value of design speed (km/h): "))
R = int(input("Enter the value of radius of curvature (m): "))
N = float(input("Enter the value of slope (as a decimal, e.g., 0.06 for 6%): "))  # Typically a decimal
W = float(input("Enter the value of width of road including extra widening (m): "))
emax = float(input("Enter the value for maximum super elevation for plain terrain (m): "))

# Calculate the rate of super elevation
ecal = (v ** 2) / (225 * R)
print("The value of Super Elevation calculated is:", ecal)

# Determine the appropriate super elevation
if ecal < emax:
    effective_emax = ecal
    print("The effective super elevation used is:", effective_emax)
else:
    effective_emax = emax
    print("The effective super elevation used is:", effective_emax)

# Calculate the length of transition curve
Ls = (effective_emax * N * W) / 2
print("The length of transition curve is:", Ls)

OUTPUT:
Enter the value of design speed (km/h): 65
Enter the value of radius of curvature (m): 220
Enter the value of slope (as a decimal, e.g., 0.06 for 6%): 150
Enter the value of width of road including extra widening (m): 7.5
Enter the value for maximum super elevation for plain terrain (m): 0.07
The value of Super Elevation calculated is: 0.08535353535353535
The effective super elevation used is: 0.07
The length of transition curve is: 39.37500000000001


Q.2) # Input Constants
R = int(input("Constant R: "))
C = int(input("Constant C: "))

# Input Data Sizes
A = int(input("Total data values for EWL constant: "))
B = int(input("Total data values for AADT: "))

# Initialize Lists
EWL_Constant = []
AADT = []

# Input EWL Constants
for i in range(A):
    ewl_value = float(input(f"Enter EWL Constant {i + 1}: "))
    EWL_Constant.append(ewl_value)

# Input AADT Values
for j in range(B):
    aadt_value = float(input(f"Enter AADT value {j + 1}: "))
    AADT.append(aadt_value)

# Calculate the Dot Product
product = np.dot(EWL_Constant, AADT)

# Calculate Total EWL
Total_EWL = product
print("Total EWL:", Total_EWL)

# EWL after 60 years
print("EWL after 60 years:", Total_EWL * 1.6)

# Calculate Traffic Index
T1 = 1.35 * (((1.6 * Total_EWL) + (product / 2)) ** 0.11)
print("Traffic Index:", T1)

# Calculate Pavement Thickness
Thickness = 0.166 * T1 * (90 - R) / (C ** 0.2)
print("Pavement Thickness:", Thickness, "cm")

OUTPUT:
Constant R: 48
Constant C: 16
Total data values for EWL constant: 4
Total data values for AADT: 4
Enter EWL Constant 1: 330
Enter EWL Constant 2: 1070
Enter EWL Constant 3: 2460
Enter EWL Constant 4: 4620
Enter AADT value 1: 3750
Enter AADT value 2: 470
Enter AADT value 3: 320
Enter AADT value 4: 120
Total EWL: 3082000.0
EWL after 60 years: 4931200.0
Traffic Index: 7.577910657490486
Pavement Thickness: 30.34470100391634 cm



Q.3) # Input for load, tire pressure, and number of layers
P = float(input("Load in kg: "))
p = float(input("Tire pressure in kg/cm²: "))
M = int(input("Total number of layers in a given pavement: "))
pi = 3.14159
CBR = []

# Loop to input CBR values and calculate thickness for each layer
for i in range(1, M + 1):
    CBR_value = float(input(f"California Bearing Ratio of layer {i} in %: "))  # Input for each layer's CBR
    CBR.append(CBR_value)
    
    # Calculate the thickness
    T = ((1.75 * P) / CBR_value - (P / (p * pi))) ** 0.5
    print("Thickness above this layer:", T, "cm")

# Mention the bitumen layer thickness
print("Given that there is a bitumen layer of 4 cm.")


OUTPUT:
Load in kg: 4085
Tire pressure in kg/cm²: 2.7
Total number of layers in a given pavement: 3
California Bearing Ratio of layer 1 in %: 4.38
Thickness above layer 1: 33.92 cm
California Bearing Ratio of layer 2 in %: 6
Thickness above layer 2: 26.64 cm
California Bearing Ratio of layer 3 in %: 12
Thickness above layer 3: 10.68 cm
Given that there is a bitumen layer of 4 cm.
