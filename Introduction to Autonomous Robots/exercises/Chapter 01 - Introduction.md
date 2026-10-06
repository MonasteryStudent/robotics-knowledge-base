## Exercise 1 - Sensors for Ratslife

### Question

What kind of sensors do you need to solve the “Ratslife” game?
Think both about trivial and close-to-optimal approaches.

### Answer

1. **Random movement without navigation sensors:**  
   A robot that drives and mechanically bounces off walls may
   reach a feeder by chance. No navigation sensors are required,
   assuming that receiving energy happens automatically.
   However, the robot may run out of energy before finding a feeder.

2. **Wall following:**  
   A whisker or an infrared, ultrasonic, or laser distance sensor
   allows the robot to detect walls and follow a wall on its right.
   A whisker typically detects contact rather than measuring distance.
   This strategy explores the maze except for disconnected wall
   islands, but does not necessarily find short routes between feeders.

3. **Mapping and planned navigation:**  
   A camera allows the robot to identify environmental markers,
   distance sensors help it avoid walls, and wheel encoders provide
   measurements for odometry. Together with computation and memory,
   these capabilities allow the robot to build a map, locate feeders,
   and plan short routes between them. Odometry is imperfect because
   wheel slip and other errors affect movement estimates.

### Takeaway

The necessary sensors depend on the information required by the
robot's strategy. Additional sensing can support more efficient
behavior, but does not guarantee an optimal solution.

## Exercise 2 - Robots at Home

### Question

What devices in your home could be considered robots? Why and why not?

### Answer

1. **Washing machine:**  
   A washing machine senses conditions such as water level and
   temperature, processes this information, and acts through
   motors, valves, and a heater. Once started, it performs its
   task without continuous human control. Under a broad definition,
   it could therefore be considered a robot. However, I would
   usually call it an automated machine because it operates
   within a tightly constrained setting.

2. **Robot vacuum cleaner:**  
   A robot vacuum cleaner senses its surroundings and uses this
   information to navigate, avoid obstacles, and clean the floor
   without continuous human guidance. It can therefore be
   classified as a robot, even though it is specialized in
   a single main task.

### Takeaway

The boundary between automated machines and robots is difficult
to draw. Here, the main distinction is between controlling a
constrained process and navigating a changing environment.

## Exercise 3 - A Mechanical Clock

### Question

Is a mechanical clock a robot? Why and why not?

### Answer

I would classify a conventional mechanical clock as an automated
mechanism rather than a robot. It moves its hands through a
mechanical process, but does not use sensory information about
its surroundings to guide its actions.

### Takeaway

Under my working definition, physical movement and automatic operation 
alone are not sufficient to qualify a machine as a robot.

### Question

Which industries have been recently revolutionized by robotics?
Into which industries were robots introduced first?
Which industries are currently being transformed?

### Answer

| Part of the question | Examples |
| --- | --- |
| Early adoption | Automotive manufacturing was an early adopter. In 1961, General Motors installed Unimate to handle hot die-cast metal parts. Robots later became important for welding, painting, and material handling. |
| Major changes through robotics | Automotive and electronics manufacturing use robots extensively for repetitive production tasks, improving speed, precision, and consistency. |
| Current transformation | Logistics uses mobile robots to transport goods in warehouses. Healthcare uses surgical robots to assist surgeons during procedures. These applications are changing particular tasks rather than automating entire industries. |

### Takeaway

Robotics first became established in industrial manufacturing
and has since expanded into areas such as logistics and healthcare.

### Sources

- [IFR: Robot History](https://ifr.org/robot-history)
- [IFR: World Robotics 2025 – Industrial Robots Summary](https://ifr.org/ifr-press-releases/news/global-robot-demand-in-factories-doubles-over-10-years)
- [IFR: World Robotics 2025 – Service and Medical Robots Summary](https://ifr.org/ifr-press-releases/news/service-robots-see-global-growth-boom)

## Exercise 5 - Sensing While Grasping

### Question

What sensors are you using when you grasp an object?
Enumerate them all. Which ones are absolutely necessary
and which one could you live without?

### Answer

Using the example of grasping a glass:

| Sensory system | Information provided | Is it necessary? |
| --- | --- | --- |
| Vision | The glass's location, shape, size, and contents | Not continuously necessary if its position is already known and it remains stationary. Touch can support a search if its position is unknown. |
| Touch receptors in the skin | Contact, pressure, and slipping | Important for reliable grip control, especially without vision. Visual feedback may compensate partly for its absence. |
| Proprioceptive receptors in muscles, tendons, and joints | Hand and arm position, movement, and muscle tension | Important for guiding movement without looking at the hand. Vision may compensate partly for its absence. |
| Temperature receptors | How hot or cold the glass is | Not required for grasping an ordinary glass, but useful for avoiding unsafe temperatures. |
| Pain receptors | Potentially harmful contact, heat, or pressure | Not required for the grasp itself, but important for protection. |
| Vestibular system in the inner ear | Head movement and orientation relative to gravity | Helps maintain body balance, especially while carrying the glass, but is not essential for a simple grasp while seated and supported. |

### Takeaway

Which senses are necessary depends on the task, prior knowledge,
and available alternatives. A familiar, stationary glass can
be grasped without continuous vision, while an unfamiliar or
moved object requires updated information or a different strategy.

## Exercise 6 - Planning for Vacuuming and Mowing

### Question

Think about robots vacuuming your floor or mowing your lawn.
Do they use any planning? Is planning necessary? Why or why not?

### Answer

Depending on their design, these robots may use planning or
operate through reactive behavior, such as moving forward
and turning when an obstacle is detected.

Planning is not strictly necessary for basic operation.
A reactive robot may eventually cover the accessible area,
but it can revisit some places repeatedly and miss others
during a limited operating time.

With a map, an estimate of its position, and a record of
covered areas, a robot can plan a systematic coverage route.
This can reduce missed areas, unnecessary repetition,
operating time, and energy consumption.

### Takeaway

Planning is not essential for basic vacuuming or mowing,
but it supports more efficient and reliable coverage.

## Exercise 7 - Sensors for an Autonomous Car

### Question

What kind of sensors would you need in a car that drives completely
autonomously? Think first about the information the car needs,
then discuss sensors that could capture it.

### Answer

| Required information | Possible sensors |
| --- | --- |
| Road layout, lane markings, traffic signs, and traffic lights | Cameras |
| Locations and distances of vehicles, pedestrians, and obstacles | Cameras, lidar, and radar |
| Relative speed of nearby vehicles and obstacles | Radar; successive camera or lidar observations |
| Nearby obstacles during parking | Ultrasonic sensors and cameras |
| Geographic position | A Global Navigation Satellite System (GNSS), such as GPS or Galileo |
| Acceleration and turning motion | An Inertial Measurement Unit (IMU), containing accelerometers and gyroscopes |
| Speed and distance travelled | Wheel-speed sensors or wheel encoders |
| Steering angle and operating condition | Steering-angle, battery or fuel, and other internal sensors |

GNSS provides a global position reference. IMU and wheel
measurements help estimate movement between position updates.
Combined with environmental observations, they support
estimation of the car's position and orientation.

### Takeaway

An autonomous car needs information about both its surroundings
and its own state. Sensors provide measurements; software must
interpret them and use them for driving decisions.