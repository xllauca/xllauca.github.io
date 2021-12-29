---
layout: post
title:  Cómo prepararse y superar el examen de Certfied Ethical Hacker (CEH) Practical.
summary: "En este post te compartire algunas claves para superar el examen (CEH Practical) en base a mi propia experiencia."
author: xllauca
date: '2021-12-29 00:00:00 +0530'
category: certifications
thumbnail: /assets/img/posts/cehp.jpg
keywords: hacking,ec-council,ceh
permalink: /blog/how-pass-cehp/
usemathjax: true
---
<br />

### 0x0. **Intro**
Este post resume  mis conclusiones sobre cómo aprobar el examen de CEH Practical en base a mi experiencia, las recomendaciones de <a target="_blank" href="https://www.linkedin.com/pulse/rese%C3%B1a-del-examen-para-la-certificaci%C3%B3n-ceh-practical-jorge-moya/?originalSubdomain=es">Jorge Moya</a>  y las mentorías de mis amigos de la Comunidad de Seguridad Ofensiva <a target="_blank" href="https://www.pwn.ec/">PwnEC</a>, las cuales fueron de gran ayuda durante mi proceso de preparación.

Mi intención no es incluir preguntas reales del examen, sino dar consejos a los candidatos al examen sobre cómo aprobarlo.

### 0x1. **¿Que conocimientos Teóricos y prácticos de seguridad informática debo tener?**
* **Reconocimiento**
* **Enumeración**
* **Análisis**
* **Explotación**
* **Redes (protocolos, puertos, servicios)**
* **Diferentes tipos de ataques de criptografía**
* **Manejo de sistemas operativos (Linux, Windows)**
* **Ataques a aplicaciones web**
* **Ataques de inyección SQL**


### 0x2. **Recomendaciones antes de rendir el Examen.**
* **Practicar en la plataforma de <a target="_blank" href="https://portswigger.net/web-security">Web Security Academy</a>, "por lo menos el módulo de SQL injection".**
* **Resolver los retos de Damn Vulnerable Web Application<a target="_blank" href="https://dvwa.co.uk/"> (DVWA)</a>, "SQL Injection".**
* **Practicar los diferentes tipos de algotirmos de Cifrado/Decifrado con el software <a target="_blank" href="https://www.c-sharpcorner.com/article/encryption-decryption-using-cryptool/">CrypTool</a>.**
* **Saber <a target="_blank" href="https://nored0x.github.io/red-teaming/active-directory-domain-enumeration-part-1/">enumerar</a> objetos de Active Directory.**
* **Resolver la máquina <a target="_blank" href="https://app.hackthebox.com/machines/Explore">Explore</a> de la plataforma de HackTheBox.**
* **Resolver CTF donde se utilice Wireshark <a target="_blank" href="https://res260.medium.com/ihack-2019-fun-in-the-wireshark-world-writeup-61c4d09a441a">iHack 2019</a> y <a target="_blank" href="https://www.petermstewart.net/dfa-ccsc-spring-2020-ctf-wireshark-https-pcapng-write-up/">DFA/CCSC Spring 2020 CTF</a>.**


### 0x3. **¿Que herramientas debo por lo menos saber utilizar para el Examen?**


<table class="table" border="1">
  <thead class="thead-dark">
    <tr>
      <th scope="col">Category</th>
      <th scope="col">Tool</th>
    </tr>
  </thead>
  <tbody>
      <tr>
        <th scope="row" rowspan=2>Scanning</th>
        <td><a target="_blank" href="https://nmap.org/">Nmap</a> (Linux) </td>
      </tr> 
      <tr>
         <th><a target="_blank" href="https://nmap.org/zenmap/">Zenmap </a> (Windows)</th>
      </tr>
      <tr>
        <th scope="row" rowspan=1>Sniffing</th>
        <td><a target="_blank" href="https://www.wireshark.org/">Wireshark</a> (Wondows/Linux) </td>
      </tr> 
      <tr>
        <th scope="row" rowspan=1>SQL Injection tools </th>
        <td><a target="_blank" href="https://sqlmap.org/">Sqlmap</a>(Linux) </td>
      </tr> 
      <tr>
        <th scope="row" rowspan=3>Password brute-forcing tools</th>
        <td><a target="_blank" href="https://github.com/vanhauser-thc/thc-hydra">Hydra</a> (Linux) </td>
      </tr> 
      <tr>
        <td><a target="_blank" href="https://crackstation.net/">CrackStation</a> (Web)</td>
      </tr> 
      <tr>
         <th><a target="_blank" href="https://www.openwall.com/john/">John The Ripper</a> (Linux) </th>
      </tr>
      <tr>
        <th scope="row" rowspan=1>WordPress Hacking </th>
        <td><a target="_blank" href="https://wpscan.com/wordpress-security-scanner">Wpscan</a> (Linux) </td>
      </tr> 
      <tr>
        <th  scope="row" rowspan=3>Criptography</th>
        <td><a target="_blank" href="https://www.slavasoft.com/hashcalc/">HashCalc</a> (Windows)</td>
        <tr>
        <td> <a target="_blank" href="https://www.guru99.com/how-to-make-your-data-safe-using-cryptography.html">Cryptool</a> (Windows)</td>
        </tr>
      </tr> 
      <tr>
         <th><a target="_blank" href="https://www.veracrypt.fr/code/VeraCrypt/">Veracrypt</a> (Windows)</th>
      </tr>
      <tr>
        <th scope="row" rowspan=2>Proxy tools</th>
        <td><a target="_blank" href="https://portswigger.net/burp">Burp Suite</a> (Linux/Windows) </td>
      </tr> 
      <tr>
         <th><a target="_blank" href="https://www.zaproxy.org/">OWASP ZAP</a> (Linux/Windows)</th>
      </tr>
  </tbody>
</table>

### 0x4. **¿Es el examen a libro abierto?**


**Sí, yo tenia la libertad de buscar información en internet y/o consultar en los apuntes de mi computador,<span style="color:green"> incluso instalé software adicional en una maquina Windows</span>.**


### 0x5. **¿Recomendaciones durante el examen?**

**El candidato al examen tiene control directo sobre dos máquinas "que se acceden desde el navegador": una es una máquina Parrot Security OS, y la otra es Windows (probablemente Windows 10).**

**Entonces él/ella tiene que descubrir cuáles son los dispositivos alojados dentro de la red. Posiblemente sean las siguientes:**

* **Windows 10**
* **Windows Server 2016**
* **Windows Server 2019**
* **Movil (Android)**

**Existe una carpeta que contiene los archivos de listas de contraseñas y otras herramientas útiles del (CEH "Teórico") que están disponibles durante el examen. En mi caso, reutilicé las listas de contraseñas en lugar de generar las mías propias.**

**Existe un panel de la derecha, donde están las instrucciones y las 20 preguntas. Al final de cada pregunta hay botones de radio con opciones o un cuadro de texto para introducir la respuesta correcta. Una vez contestadas todas las respuestas y terminado el examen, hay que avisar al supervisor y hacer clic en "Submit".**

**Se utiliza el mismo entorno para cada pregunta. Sin embargo, la mayoría de las preguntas son independientes entre sí, por lo que no es necesario resolver una pregunta para continuar con otra. Puede hacerlas en cualquier orden.**

<span style="color:Red">Nota: Verifica que tus respuestas estén de acuerdo a lo que solicitan (case sensitive, formatos, solo numeros/letras, etc)</span>.


### 0x6. **¿Cuánto tiempo se tarda en obtener los resultados del examen? ¿O se corrige inmediatamente?**


El examen se corrige inmediatamente, en función de tus datos.

Una vez que termines el examen, encontrarás en la plataforma de Aspen los resultados del CEH Práctico.


