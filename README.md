//@version=4
study("Linear Correlation Oscillator","LCO")
length = input(14),src = input(close)
//----
cmla=0.,cmlb=0.,cmlc=0.
cmla := nz(cmla[1]) + src
cmlb := nz(cmlb[1]) + cmla
cmlc := nz(cmlc[1]) + src*src
//----
sum = cmlb - cmlb[length]
a = (length*cmla-sum[1])
b = cmla - cmla[length]
c = cmlc - cmlc[length]
//----
num = (a - b*(length+1)/2)/length
vary = c/length - pow(b/length,2)
var varx = (length*length - 1)/12
cor = num/sqrt(vary*varx)
//----
plot(cor,"ROsc",#2157f3)
