# Task 1
# Write your get_y() function here
def get_y(m,b,x):
  y = (m*x) + b
  return y
# Uncomment each print() statement to check your work. Each of the following should print True
print(get_y(1, 0, 7) == 7)
print(get_y(5, 10, 3) == 25)


# Tasks 2 and 3
# Write your calculate_error() function here
def calculate_error(m,b,point):
  x_point = point[0]
  y_point = point[1]
  y_value = get_y(m,b,x_point)
  difference = y_value - y_point
  return abs(difference)

# Task 4
# Uncomment each print() statement and check the output against the expected result

# this is a line that looks like y = x, so (3, 3) should lie on it. thus, error should be 0:
print(calculate_error(1, 0, (3, 3)))

# the point (3, 4) should be 1 unit away from the line y = x:
print(calculate_error(1, 0, (3, 4)))

# the point (3, 3) should be 1 unit away from the line y = x - 1:
print(calculate_error(1, -1, (3, 3)))

# the point (3, 3) should be 5 units away from the line y = -x + 1:
print(calculate_error(-1, 1, (3, 3)))

# Task 5
# Write your calculate_all_error() function here

def calculate_all_error(m,b,points):
  error_total = 0
  for point in points:
    error = calculate_error(m,b,point)
    error_total += error
  return error_total

# Task 6
# Uncomment each print() statement and check the output against the expected result
datapoints = [(1, 1), (3, 3), (5, 5), (-1, -1)]

# every point in this dataset lies upon y=x, so the total error should be zero:
print(calculate_all_error(1, 0, datapoints))

# every point in this dataset is 1 unit away from y = x + 1, so the total error should be 4:
print(calculate_all_error(1, 1, datapoints))

# every point in this dataset is 1 unit away from y = x - 1, so the total error should be 4:
print(calculate_all_error(1, -1, datapoints))

# the points in this dataset are 1, 5, 9, and 3 units away from y = -x + 1, respectively, so total error should be
# 1 + 5 + 9 + 3 = 18
print(calculate_all_error(-1, 1, datapoints))

# Tasks 8 and 9

#range of numbers to be used for each possible slopes
ms_range = [range(-100,101)]

#list of slopes but should be divided by 10
slopes_range = []

#list of possible slopes with an increment of 0.1
possible_ms = []

#formula for collecting possible_ms
for x in ms_range:
  slopes_range += x
  for num in slopes_range:
    a = float(num/10)
    possible_ms.append(a)    
print("\nPossible slopes list: \t", possible_ms)

#range of numbers to be used for each possible bs
range_bs = [range(-200,201)]

#list of y-intercepts but should be divided by 10
y_intercept_list = []

#List of possible Bs or y-intercepts with an increment of 0.1
possible_bs = []

#formula for collecting possible_bs
for x in range_bs:
  y_intercept_list += x
  for num in y_intercept_list:
    a = float(num/10)
    possible_bs.append(a)    
print("\nPossible y-intercept list: \t", possible_bs)

# Task 10
datapoints = [(1, 2), (2, 0), (3, 4), (4, 4), (5, 3)]
smallest_error = float("inf")
best_m = 0
best_b = 0

# Tasks 11 and 12
for m in possible_ms:
  for b in possible_bs:
    error = calculate_all_error(m,b,datapoints) 
    if error < smallest_error:
      best_m = m
      best_b = b
      smallest_error = error

print('\nBest m: \t', best_m, '\nBest b: \t', best_b, '\nSmallest Error: \t', smallest_error)

# Task 13

print("\nBounce of a ball with a width of 6cm:", get_y(0.4,1.6,6), "meters.")







