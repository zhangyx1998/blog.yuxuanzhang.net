---
layout: post
title: "德拜热容模型"
subtitle: "积分计算器"
header-img: "resources/physics.png"
date: 2020-04-08 18:00:00 +0800
tags:
  - Courses
  - SolidPhysics
mathjax: true
multilingual: false
---

### 计算依据

$$
    \begin{align}
    C_{V}&=9 N k_B\left(\frac{k_B T}{\hbar \omega_{D}}\right)^{3} \int_{0}^{\frac{\hbar \omega_{D}}{k_B T}} \frac{\xi^{4} e^{\xi}}{\left(e^{\xi}-1\right)^{2}} d \xi\\
        &=9 R \left(\frac{T}{\Theta_D}\right)^{3} \int_{0}^{\frac{\Theta_D}{T}} \frac{\xi^{4} e^{\xi}}{\left(e^{\xi}-1\right)^{2}} d \xi
    \r{align}
$$

> 常数包括:
> 
> &nbsp;
> 
> $k_B = 1.380649\times 10^{-23} J/K$
> 
> &nbsp;
> 
> $\hbar = 1.05457266\times 10^{-34}J·s$

---

### 计算器

<h4 style="text-align:center">$C_{V}\left(\frac{\Theta_D}{T}\right)=$<span id="result">$N/A$</span></h4>

<table style="width:100%; text-align: center; table-layout:fixed; text-align: center; vertical-align: middle;">
<col style="width: 12em">
<col>
<tbody>
<tr>
    <td>$\frac{\Theta_D}{T}=$<span id="val_N"></span></td>
    <td><input type="range" min="-1000" max="1000" value="0" id="input_N"></td>
</tr>
</tbody>
</table>
<script>
    function logInput(id_in,id_out) {
        input_elem = document.getElementById(id_in);
        output_elem = document.getElementById(id_out);
        output_elem.innerHTML = " $" + parseSN(Math.pow(10,input_elem.value/100)) +"$";
        if(typeof MathJax!=undefined){
            MathJax.typeset();
        }
    }
    function handle_pow(pow){
        return pow>0?pow:1+pow;
    }
    document.addEventListener("load",()=>{logInput("input_N","val_N");});
    document.getElementById("input_N").addEventListener('input',()=>{logInput("input_N","val_N")});
    document.getElementById("input_N").addEventListener('change',()=>{
        input_elem = document.getElementById("input_N");
        var value = Math.pow(10,input_elem.value/100);
        var result = caculate(value);
        document.getElementById("result").innerHTML = "$" + parseSN(result) + "$";
        if(typeof MathJax!=undefined){
            MathJax.typeset();
        }
    });
    function caculate(val){
        return 3 * Math.pow(val,3) * integral(int_core,{l:0,r:val},val/10000);
    }
    function int_core(xi){
        return Math.pow(xi, 4) * Math.exp(xi) / Math.pow(Math.exp(xi) - 1,2)
    }
    function integral(func, lim, step = 1e-4){
        var step = ((lim.r - lim.l) * step > 0) ? step : -step;
        var x = lim.l;
        var sum = 0;
        while(
            (step > 0 && x < lim.r)
        ||
            (step < 0 && x > lim.r)
        ){
            sum += step * func(x + step * 0.5);
            x   += step;
        }
        return sum;
    }
    function parseSN(val){
        if(val == 0) return '0';
        if(val == NaN) return 'NaN';
        if(val == Infinity) return '\\inf';
        var sign = (val >= 0)?'':'-';
            val = Math.abs(val);
        var pow = Math.log10(val);
        // var psign = (pow >= 0)?1:-1;
            pow = Math.ceil(pow) - 1;
        var num = val / Math.pow(10,pow);
        // var psign = (psign >= 0)?'':'-';
        console.log([val,num,pow]);
        return sign + num.toFixed(4).toString() + "\\times 10^{" +  pow.toString() + "}"
    }
</script>