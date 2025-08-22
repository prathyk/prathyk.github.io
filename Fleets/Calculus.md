# Limits and derivatives

A limit helps one calculate the derivative. Derivative is the rate of change of some 'y' with respect to some 'x' where y = f(x). 

df/dx is its usual notation. 

Integral is the area under the 'y' curve (given that this is a continuous function in that interval)

### Basic intuition
The area is always a summation of small derivatives. Look at the below diagram to understand how area of a circle is same as the area under the line y=2(pi)x 
![[Pasted image 20240303235811.png]]

Also look at how Integral of a f(x) can be summation derivatives at all points in x
![[Pasted image 20240304000009.png]]


## Derivative Paradox
![[Pasted image 20240304002251.png]]

Can you define velocity at an instant in time. When you want to calculate velocity of anything in practice, you always take a short change in time 'dt' and then calculate ds/dt

So, in practical life derivative or velocity is never instantaneous. But in mathematics we define derivative as approaching the slope of the tangent at that point
![[Pasted image 20240304002531.png]]

By theoretically thinking about what happens if dt approaches 0 we skip a lot of complicated maths to calculate the actual value

![[Pasted image 20240304002655.png]]

So, it is a nice approximation with many practical applications

**This is important. When you think about derivative always know that it is just an approximation

## Projecting 3d in to 2d
The volume of a cube is x^3. This is a three dimensional thing. This volume can also be represented as a 2d curve `y=x^3` The shape of the curve looks quite different from the shape of the cube. When you view something which is actually 3-dimensional from 2-dimensional perspective, some readings may match and you are actually looking at something completely different. 
Look at `y=x^3` below
![[Pasted image 20240304004401.png]]

## Power Rule
![[Pasted image 20240304004456.png]]

Many times we just think if this as symbolic manipulation which understanding the deep reasoning behind it. ChatGPT and other LLMs are really good in symbolic manipulation. They memorize the various pathways of symbolic manipulations. 

## Geometrical representations of some pure funtions

`f(x) = 1/x`
![[Pasted image 20240304010324.png]]

`f(x) = sqrt(x)`
![[Pasted image 20240304010348.png]]

### Sine and Cosines

`Sin(Θ) = Oppsite / Hypoteneus`
`Cos(Θ) = Adjacent / Hypoteneus`

![[Pasted image 20240304010653.png]]

Derivative of sin is same as cosine
![[Pasted image 20240304010614.png]]

## Sum Rule
![[Pasted image 20240304145752.png]]
![[Pasted image 20240304145831.png]]
## Product Rule

![[Pasted image 20240304145847.png]]

![[Pasted image 20240304145916.png]]

## Product rule in terms of Sum rule

`f(x) = g(x).h(x)` can be written as 
`f(x) = h(x) + h(x) + h(x)....g(x) times`
`f'(x) = h'(x) + h'(x)+....g(x) times`
`f'(x) = g(x).h'(x)`
Note that this does not work because g(x) is not a constant

## Chain Rule
![[Pasted image 20240304163334.png]]

![[Pasted image 20240304163457.png]]

![[Pasted image 20240304163530.png]]
The above picture shows chain rule application in function composition


# Euler number - e

`e` is defined as follows:
It is that number where `e^x` derivative is itself
Look at below to understand how slope of `e^x` is always `e^x` 
![[Pasted image 20240304165510.png]]

For every unit change in 't' the y value changes by e^t

Note that every exponential's derivative is proportional to itself

![[Pasted image 20240304170249.png]]
![[Pasted image 20240304170318.png]]

![[Pasted image 20240304170335.png]]

`e` is that number where that constant is '1'

![[Pasted image 20240304170503.png]]

![[Pasted image 20240304170521.png]]

![[Pasted image 20240304170624.png]]

![[Pasted image 20240304170705.png]]
## Ln (x)
`ln(2) ` is defined as that number which gives `2` when raised to the power of `e` 
`ln(x) ` is defined as that number which gives `x` when raised to the power of `e` 

![[Pasted image 20240304171202.png]]

![[Pasted image 20240304171354.png]]

So, if I write `2^x` as `e^ln(2^x) = e^(x.ln(2))` and then its derivative would be:
`ln(2)e^(x.ln(2)) = ln(2).2^x` 

So, derivative of `a^x` is always proportional to itself:

`d/dx(a^x) = ln(a).a^x` 

In fact, `log` is a function with following property:

![[Pasted image 20240304172231.png]]

In general,

`x = y^(log[base y] x)`

## Expressing exponential growth in terms of `e`

As seen above, although any exponential can be written as any other exponential, we usually choose it express it in terms of `e` because of this special property of `e` that:
`d/dx (e^x) = e^x` 

In all natural phenomena, the rate of growth is always proportional to the thing that is growing. So, those are always expressed as exponentials of `e`. For e.g. rate of growth in population, rate of decrease in temperature of water etc...

## Implicit Derivatives

For a circle with radius 5 the rate of change of y w.r.t x is obtained by considering how the entire function of S(x,y) changes w.r.t x and y
![[Pasted image 20240304175106.png]]


# Integrals

For the velocity graph, the area under the graph represents the distance travelled, approximately
![[Pasted image 20240304185601.png]]

So, you can calculate the anti-derivatives at 0 and T and then subtract both.
![[Pasted image 20240304185707.png]]

Integrals measure the signed area between the graph and the axis
![[Pasted image 20240304185824.png]]