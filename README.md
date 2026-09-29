# Simulación en Gazebo — Rover con lidar sobre el cráter Gale de Marte

Modelos de simulación para Gazebo que reúnen un rover tipo **Perseverance (NASA Mars 2020)** equipado con IMU y lidar, y un fragmento del terreno del **cráter Gale** en Marte. Sirven como base para probar navegación y percepción de un rover en un terreno marciano.

## Contenido

| Carpeta | Qué es |
| --- | --- |
| `Rover lidar/` | Modelo del rover (`nasa_perseverance_sensor_config_1`): chasis de 1025 kg con malla del Perseverance, seis ruedas con articulaciones de giro libre, una **IMU** a 50 Hz con ruido gaussiano y un **lidar** de 640 muestras en un arco de 180° con alcance de 0,1 a 30 m, publicado en el tópico `/scan`. |
| `Mars Gale Crater Patch 1(1)/` | Terreno estático del cráter Gale (malla `gale_crater_patch1.stl`) con texturas de arena y roca. |

## Cómo usarlo

1. Instala Gazebo.
2. Agrega esta carpeta a la ruta de modelos:

   ```bash
   git clone https://github.com/Alejob12/Simulacion_Gazebo.git
   export GAZEBO_MODEL_PATH=$GAZEBO_MODEL_PATH:$PWD/Simulacion_Gazebo   # Gazebo clásico
   # export GZ_SIM_RESOURCE_PATH=$GZ_SIM_RESOURCE_PATH:$PWD/Simulacion_Gazebo   # gz-sim
   ```

3. Abre Gazebo, inserta el terreno y el rover desde el panel de modelos y verifica la lectura del lidar en `/scan`.

## Compatibilidad

Los dos modelos están escritos para versiones distintas de SDF:

- El rover usa **SDF 1.6** y el plugin `libgazebo_ros_laser.so`, propio de **Gazebo clásico** con ROS.
- El terreno usa **SDF 1.10** con materiales PBR, pensado para **gz-sim** (Gazebo moderno).

Para usarlos juntos en un mismo mundo hay que llevar ambos a la misma versión de Gazebo; esa alineación es el siguiente paso natural del proyecto.

## Créditos

- El modelo del terreno (`Gale Crater Patch1`) es obra de Jasmeet Singh, según consta en su `model.config`.
- La malla del rover corresponde al modelo público del rover Perseverance de la misión NASA Mars 2020.
- La configuración de sensores (IMU y lidar) y el ensamblaje de la simulación son del autor de este repositorio.

## Autor

**Alejandro Bernal** — Ingeniería de Sistemas e Industrial, Universidad de los Andes.
