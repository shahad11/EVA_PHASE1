## GoogLeNet receptive field calculations

>I have selected input size as 228x228 as we are using 7x7 kernals with strides as 2. i am assuming the padding will be one, to get the 
output image size as 112. there can be two possibility 1) input image size as 224x224 with strides 2 and padding 3 2) above combination

```

(Kernal,p,s)  Operation			Input size		Output size	       RF		
JumpIN		

		Start			228			228			1						1

(7x7,1,2)	Conv			228			112			7						1
(3x3,1,2)	MaxPool			112			56			11						2
		1X1
(3x3,1,1)	Conv			56			56			19						4
(3x3,1,2)	MaxPool			56			28			27						4



Inception(3a)
		1X1															8
(3x3,1,1)	1X1 -> Conv		28			28			43						8			
(5x5,2,1)	1X1 -> Conv		28			28			59						8	


Inception(3b)
			1X1														8
(3x3,1,1)	1X1 -> Conv		28			28			75						8			
(5x5,2,1)	1X1 -> Conv		28			28			91						8	




(3x3,1,2)	MaxPool			28			14			107						8			



Inception(4a)
			1X1														16									
(3x3,1,1)	1X1 -> Conv		14			14			139						16			
(5x5,2,1)	1X1 -> Conv		14			14			171						16	


Inception(4b)
			1X1														16
(3x3,1,1)	1X1 -> Conv		14			14			203						16			
(5x5,2,1)	1X1 -> Conv		14			14			235						16	
	

Inception(4c)
			1X1														16
(3x3,1,1)	1X1 -> Conv		14			14			267						16			
(5x5,2,1)	1X1 -> Conv		14			14			299						16	


Inception(4d)
			1X1														16
(3x3,1,1)	1X1 -> Conv		14			14			331						16			
(5x5,2,1)	1X1 -> Conv		14			14			363						16	


Inception(4e)
			1X1														16
(3x3,1,1)	1X1 -> Conv		14			14			395						16			
(5x5,2,1)	1X1 -> Conv		14			14			427						16	




(3x3,1,2)	MaxPool			14			7			459						16			



Inception(5a)
			1X1														32
(3x3,1,1)	1X1 -> Conv		7			7			523						32			
(5x5,2,1)	1X1 -> Conv		7			7			587						32	


Inception(5b)
			1X1										         			32
(3x3,1,1)	1X1 -> Conv		7			7			651						32			
(5x5,2,1)	1X1 -> Conv		7			7			715						32	




(7x7,1,1)	AvgPool			7			1			715						32



```
