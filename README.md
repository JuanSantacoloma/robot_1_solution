# Modelos de robots para prueba de modelo cinematico

En este paquete se encuentra de forma condensada la solución del robot 1 propuesto por Jose Fajardo que se encuentra en el repositorio : https://github.com/jmfajardod/robots_rycsv_description y en el repositorio: https://github.com/jmfajardod/models_robots_rycsv_py .

## Comandos para replicar resultados
Primero hay con usar el comando catkin build con el paquete:
> <code> catkin build robot_1_solution  </code>

Luego realizar source del catkin
> <code> source ~/catkin_ws/devel/setup.bash </code>

Posterior se sugiere usar el archivo launch robot_test_simulation.launch y así visualizar el robot tanto en Rviz como en Gazebo:

> <code> roslaunch robot_1_solution robot_test_simulation.launch </code>

Y por ultimo se ejecutara el nodo que nos permite crear el topico > <code>/cmd_vel</code> el robot:
> <code> rosrun robot_1_solution node_1.py  </code>

Para verificar que el proceso haya funcionado bien de debe verificar que los topicos activos sean los siguientes:
> <code> /clicked_point </code>
> <code> /clock </code>
> <code> /cmd_vel </code>
> <code> /front_wheel_ctrl/command </code>
> <code> /gazebo/link_states </code>
> <code> /gazebo/model_states </code>
> <code> /gazebo/parameter_descriptions </code>
> <code> /gazebo/parameter_updates </code>
> <code> /gazebo/set_link_state </code>
> <code> /gazebo/set_model_state </code>
> <code> /initialpose </code>
> <code> /joint_states </code>
> <code> /left_wheel_ctrl/command </code>
> <code> /move_base_simple/goal </code>
> <code> /right_wheel_ctrl/command </code>
> <code> /rosout </code>
> <code> /rosout_agg </code>
> <code> /tf </code>
> <code> /tf_static  </code>

Para mover el robot se deben enviar mensajes tipo Twist al topico > <code> /cmd_vel  </code>, esto se puede realizar con el comando:
> <code> rostopic pub -1 /cmd_vel  </code>


# En caso de errores

Si al tratar de iniciar la simulación se obtiene el error:

> <code> **Could not load controller 'left_wheel_ctrl' because controller type 'velocity_controllers/JointVelocityController' does not exist.** [ERROR] </code>

Por favor revisar que se tenga instalado el paquete ros_control, para realizar la instalación es necesesario ejecutar el comando (Reemplazar $DISTRO$ con la distribución que se tenga de ROS kinetic, melodic o noetic):

> <code> sudo apt-get install ros-$DISTRO$-ros-control ros-$DISTRO$-ros-controllers </code>


## Robot 1

El robot 1 tiene tres ruedas tipo suecas con los rodillos a 90 grados:

<img src="https://render.githubusercontent.com/render/math?math=\gamma=0">

Las ruedas estan en las esquinas de un triangulo rectangulo de lado <img src="https://render.githubusercontent.com/render/math?math=l=0.5">

La configuración de las ruedas y del sistema de referencia del robot es como se muestra en la imagen inferior:

<img src="./imgs/Esquema_robot_1.png" heigh=200 alt="Esquema_robot_1">

Con esta configuración se obtienen los siguientes parametros:

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky"><img src="https://render.githubusercontent.com/render/math?math=Rueda"></th>
    <th class="tg-0pky"><img src="https://render.githubusercontent.com/render/math?math=l"></th>
    <th class="tg-0pky"><img src="https://render.githubusercontent.com/render/math?math=\alpha"></th>
    <th class="tg-0pky"><img src="https://render.githubusercontent.com/render/math?math=\beta"></th>
    <th class="tg-0pky"><img src="https://render.githubusercontent.com/render/math?math=\gamma"></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0pky"><img src="https://render.githubusercontent.com/render/math?math=front"></td>
    <td class="tg-0pky"><img src="https://render.githubusercontent.com/render/math?math=0.433"></td>
    <td class="tg-0pky"><img src="https://render.githubusercontent.com/render/math?math=0.0"></td>
    <td class="tg-0pky"><img src="https://render.githubusercontent.com/render/math?math=0.0"></td>
    <td class="tg-0pky"><span style="font-weight:400;font-style:normal"><img src="https://render.githubusercontent.com/render/math?math=0.0"></span></td>
  </tr>
  <tr>
    <td class="tg-0pky"><img src="https://render.githubusercontent.com/render/math?math=left"></td>
    <td class="tg-0pky"><img src="https://render.githubusercontent.com/render/math?math=0.25"></td>
    <td class="tg-0pky"><img src="https://render.githubusercontent.com/render/math?math=\frac{\pi}{2}"></td>
    <td class="tg-0pky"><span style="font-weight:400;font-style:normal"><img src="https://render.githubusercontent.com/render/math?math=0.0"></span></td>
    <td class="tg-0pky"><span style="font-weight:400;font-style:normal"><img src="https://render.githubusercontent.com/render/math?math=0.0"></span></td>
  </tr>
  <tr>
    <td class="tg-0pky"><img src="https://render.githubusercontent.com/render/math?math=right"></td>
    <td class="tg-0pky"><img src="https://render.githubusercontent.com/render/math?math=0.25"></td>
    <td class="tg-0pky"><img src="https://render.githubusercontent.com/render/math?math=-\frac{\pi}{2}"></td>
    <td class="tg-0pky"><img src="https://render.githubusercontent.com/render/math?math=\pi"></td>
    <td class="tg-0pky"><span style="font-weight:400;font-style:normal"><img src="https://render.githubusercontent.com/render/math?math=0.0"></span></td>
  </tr>
</tbody>
</table>

<br/>

<img src="./imgs/Esquema_robot_1_sol.png" heigh=200 alt="Modelo_robot_1_sol">

# robot_1_solution
