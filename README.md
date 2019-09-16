# RUL-and-SOH-estimation-of-Lithium-ion-satellite-power-systems-using-non-linear-regression-approach

![img](https://miro.medium.com/max/1024/1*mMQ9n558nvhaFHBbQW83jQ.jpeg)

Batteries are a critical part of any satellite’s power system. Batteries(mostly rechargeable) are used used to provide power:

-> during launch and after the launch of the satellite till the solar panels are deployed

-> to the spacecraft, it’s equipment and payload during shadow phase

-> for communication and data transfer

-> to maintain the electronics at a specific temperature

Batteries with higher gravimetric(higher mass) and volumetric(higher volume) energy densities lead to lesser mass and volume for the power systems and thereby increase payload and mission capabilities.

![img2](https://miro.medium.com/max/879/1*IBRM01ok9k1Ndp9hh_YG8A.png)

That is why Lithium-ion batteries are so extensively used in satellites as power systems. A NiCD(nickel-cadmium) battery pack has as much as 50% less energy density as Li-ion batteries.

Batteries tend to degrade after continuous charge and discharge cycles. There is a need to develop an accurate remaining useful life(RUL) estimation system for Li-ion batteries. 

The estimated RUL can provide useful information to the ‘health management and maintenance’ and the ‘ground reliability assessment’ team. From this information, the maintenance team can plan the maintenance task schedule.


## The approach of Lithium-ion battery RUL estimation :

1) Model-based approach

2) Data-driven approach

The model-based approach makes use of battery characteristics and physical structure. The data-driven approach is not based on accurately modeling the physics of a system like the model-based approach but instead estimates RUL based on historical data.

## The Dataset :

The dataset used for this project can be downloaded [here](https://ti.arc.nasa.gov/tech/dash/groups/pcoe/prognostic-datarepository/)

This data has been collected from prognostics testbed at the NASA Ames Prognostics Center of Excellence (PCoE). The experiments were stopped when the batteries reached the end of life criterion, which was a 30% fade in
rated capacity (from 2 A·h to 1.4 A·h). This time-series data can be used for the development of prognostic algorithms that can accurately predict the RUL of Li-ion batteries.

## Exploratory data analysis :

The battery data was provided in .mat format, I wrote a python script that parses .mat files and converts them into JSON objects.
The script can be found here.
For visualization, I used the Matplotlib library.

Let us take a look at the battery capacity degradation at different ambient temperatures.

![image1](https://miro.medium.com/max/730/1*XdPKdbWJ1PS53g20VcMjLA.png)
![image2](https://miro.medium.com/max/725/1*dFPF9O4rGe7v_5DYdIpTYQ.png)
![image3](https://miro.medium.com/max/724/1*Q-nReUjUBcRGwZFUBRX9ow.png)

From the above diagrams, it can be noted that the capacity is not always continuously decreasing with every discharge cycle. Sometimes the capacity increases resulting in distinctive spikes.

![image4](https://miro.medium.com/max/725/1*4zev1elMClKNo00dyc9i4g.png)

## Charging performance :

![imag](https://miro.medium.com/max/1348/1*TQxOZsAwEDF0RHfgNuoz5A.png)

![imag2](https://miro.medium.com/max/1350/1*apouRz39F1UelhDIFKjP9w.png)

![imag3](https://miro.medium.com/max/1348/1*HChjJ9q_0Uxnle-8SwBkpw.png)

![imag4](https://miro.medium.com/max/892/1*tUGlC5m89oxrR13o3i7EfQ.png)

![imag5](https://miro.medium.com/max/891/1*q0pMwQCh_uPuCYWGlsiZhg.png)

## Discharge performance :

![imag6](https://miro.medium.com/max/1348/1*AwBysLNqCnTiKxGA-9cZ5Q.png)

![imag7](https://miro.medium.com/max/1347/1*j2_QhkaqR0-sVaaAug2IiA.png)

![imag8](https://miro.medium.com/max/1347/1*4LhFwFAi0VBUlhP8SUaosg.png)

![imag9](https://miro.medium.com/max/899/1*wcZBHCusb1yppIZ3Hz0t3Q.png)

![imag10](https://miro.medium.com/max/907/1*LksxMEaVTq3yc2ehWYH6eg.png)

## Model building :

Now let us build a model to fit the data but first, we need to identify and remove outliers to increase prediction performance.

![imag11](https://miro.medium.com/max/404/1*W4r_n-n0zR6IpgZ8xFUN6A.png)

The outliers were detected using the rolling standard deviation method. 

![imge](https://miro.medium.com/max/724/1*haeVlVvD-6FC7ZqJXeXQBQ.png)

![imge](https://miro.medium.com/max/407/1*VJCmxrwzJmy0cH8VKhPGaw.png)

![imge](https://miro.medium.com/max/396/1*QBhBDiTxliui7Xo3rQncPA.gif)

![imge](https://miro.medium.com/max/725/1*Es-IvwgCdbO57k59Aae6WQ.png)

![imge](https://miro.medium.com/max/407/1*VJCmxrwzJmy0cH8VKhPGaw.png)

![imge](https://miro.medium.com/max/725/1*TkVJMHMc769airTwkrRDFA.png)

![imge](https://miro.medium.com/max/414/1*-tqYkRkzUDz8PiraWV4YPQ.png)

![imge](https://miro.medium.com/max/725/1*ZhGmBxwJyvY3299h7PePNw.png)

![imge](https://miro.medium.com/max/407/1*2AEk-o9yCxnPGb4-UGgoRg.png)

![imge](https://miro.medium.com/max/725/1*lSt9D_khDGa5BjB-iVgKIg.png)

![imge](https://miro.medium.com/max/404/1*Qhi9zhH7oMirtvzCPH-7PA.png)

![imge](https://miro.medium.com/max/724/1*uKKrldaoUmBLx1N1mtQBVQ.png)
