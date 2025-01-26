# Amazon Warehouse Simulation
Simulation of a Amazon warehouse Robots performing operations such as pick and place objects with the help of motion planning algorithms, and also updating the orders data remotely to Google sheets

[![Warehouse Simulation Video](https://img.youtube.com/vi/I9CYj6VW5oQ/0.jpg)](https://youtu.be/I)

[Objective](#objective)
=======================

The objective of this project is to implement a Warehouse Management System to sort packages based on incoming customer orders from different cities. To achieve this, the following tasks need to be completed:

1. The colour of any 9 packages, three of each colour, on the shelf should be identified using `Camera#1`. Either colour detection, QR decoding, or a combination of both can be used.

2. As the packages are identified, the `inventory` sheet of the `Inventory Management Spreadsheet` of the warehouse, which is a Google Spreadsheet, should be updated using the `ROS-IoT bridge`.

3. After one minute (Sim Time), a total of 9 orders will be published on the `/eyrc/vb/<unique_id>/orders` MQTT Topic at different intervals. The orders from this MQTT Topic should be retrieved using the `ROS-IoT Bridge`.

    > `<unique-id>: `This is a private ID which will be the eight-character string created during Task-1.

4. In case the `UR5#1` has multiple orders of different priorities to process, it should be ensured that High Priority orders are processed as quickly as possible, followed by Medium Priority, and then Low Priority orders to score maximum points (refer to the grading section to learn more). Packages of `red` colour will have `High Priority` symbolizing Medicines, packages of `yellow` colour will have `Medium Priority` symbolizing Food, and packages of `green` colour will have `Low Priority` symbolizing Clothes.

5. Once the package is placed on the `conveyor belt`, the `Orders Dispatched` sheet in the `Inventory Management Spreadsheet` should be updated to give the status of the packages picked up by the `UR5#1` Arm, and an email notification should be sent to the user.

6. Once the `conveyor belt` takes the packages to `UR5#2`, the `UR5#2` Arm should sort the packages based on the colour of the package identified by `Camera#1`. For example, the Red Package should go in the Red-Bin, and so on.

7. As the `UR5#2` Arm sorts the individual packages into the bins based on package colour, the `Orders Shipped` sheet of the `Warehouse Inventory Mastersheet` should be updated to give the status of the packages being picked and dropped in the bins by the `UR5#2` Arm.

8. As the run progresses, the `Warehouse Inventory Dashboard` should be updated in real-time. In the `Warehouse Inventory Mastersheet`, a separate sheet called `Dashboard` can be created to show values from other sheets in the `Warehouse Inventory Mastersheet` spreadsheet. This `Dashboard` sheet can be used as a JSON endpoint to update the `Warehouse Inventory Dashboard` in real-time.

### Step 7 Implementation
[![Warehouse Simulation Video](https://img.youtube.com/vi/b8-A88NU40Y/0.jpg)](https://youtu.be/b8)
