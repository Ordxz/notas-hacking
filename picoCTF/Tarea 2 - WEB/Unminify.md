# **Descripción**

I don't like scrolling down to read the code of my website, so I've squished it. As a bonus, my pages load faster!Browse [here](http://titan.picoctf.net:57362/), and find the flag!

# **Solución**

Al inspeccionar la página, desglosé el código del *body*, hasta que se llegó al *center* donde se encuentra todo lo siguiente, esto ya desglosado. 

```html
        <center>
            <br class="picoctf{}" />
            <br class="picoctf{}" />
            <div class="picoctf{}" style="padding-top: 30px; border-radius: 3%; box-shadow: 0 5px 10px #0000004d; width: 50%; align-self: center;">
                <img class="picoctf{}" src="hero.svg" alt="flag art" style="width: 150px; height: 150px;" />
                <div class="picoctf{}" style="width: 85%;">
                    <h2 class="picoctf{}">Welcome to my flag distribution website!</h2>
                    <div class="picoctf{}" style="width: 70%;">
                        <p class="picoctf{}">If you're reading this, your browser has succesfully received the flag.</p>
                        <p class="picoCTF{pr3tty_c0d3_743d0f9b}"></p>
                        <p class="picoctf{}">I just deliver flags, I don't know how to read them...</p>
                    </div>
                </div>
                <br class="picoctf{}" />
            </div>
        </center>
```

De tal manera que encontramos la bandera fácilmente. 

```html
<p class="picoCTF{pr3tty_c0d3_743d0f9b}"></p>
```

# **Notas adicionales**


# **Referencias**