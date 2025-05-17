# **Descripción**

We made a lot of substitutions to encrypt this. Can you decrypt it? Connect with `nc jupiter.challenges.picoctf.org 39894`.
# **Solución**

Lo primero es ingresar al servidor dado en la descripción.

```bash
┌──(chris㉿Chris)-[~]
└─$ nc jupiter.challenges.picoctf.org 39894
-------------------------------------------------------------------------------
uindbzho lsbs ao xigb ktzd - kbsygsnux_ao_u_ifsb_tzcvrz_zdktudhxgs
-------------------------------------------------------------------------------
vshpssn go hlsbs pzo, zo a lzfs ztbszrx ozar oicsplsbs, hls vinr ik hls osz. vsoarso litrand igb lszbho hidshlsb hlbigdl tind wsbairo ik oswzbzhain, ah lzr hls skksuh ik czmand go hitsbznh ik szul ihlsb'o xzbnoznr sfsn uinfauhaino. hls tzpxsbhls vsoh ik itr ksttipolzr, vsuzgos ik lao cznx xszbo znr cznx fabhgso, hls intx ugolain in rsum, znr pzo txand in hls intx bgd. hls zuuignhznh lzr vbigdlh igh ztbszrx z vie ik ricaniso, znr pzo hixand zbulahsuhgbzttx pahl hls vinso. czbtip ozh ubioo-tsddsr badlh zkh, tsznand zdzanoh hls cajjsn-czoh. ls lzr ognmsn ulssmo, z xsttip uicwtseain, z ohbzadlh vzum, zn zoushau zowsuh, znr, pahl lao zbco rbiwwsr, hls wztco ik lznro ighpzbro, bsoscvtsr zn arit. hls rabsuhib, ozhaokasr hls znulib lzr diir litr, czrs lao pzx zkh znr ozh ripn zcindoh go. ps seulzndsr z ksp pibro tzjatx. zkhsbpzbro hlsbs pzo oatsnus in vizbr hls xzulh. kib oics bszoin ib ihlsb ps rar nih vsdan hlzh dzcs ik ricaniso. ps ksth csrahzhafs, znr kah kib nihland vgh wtzuar ohzband. hls rzx pzo snrand an z osbsnahx ik ohatt znr seygaoahs vbattaznus. hls pzhsb olins wzuakauzttx; hls omx, pahligh z owsum, pzo z vsnadn accsnoahx ik gnohzansr tadlh; hls fsbx caoh in hls soose czbol pzo tams z dzgjx znr bzraznh kzvbau, lgnd kbic hls piirsr baoso antznr, znr rbzwand hls tip olibso an razwlznigo kitro. intx hls dtiic hi hls psoh, vbiirand ifsb hls gwwsb bszulso, vsuzcs cibs oicvbs sfsbx canghs, zo ak zndsbsr vx hls zwwbizul ik hls ogn.
```

Esta forma de encriptación se llama sustitución, el cual es uno de los métodos criptográficos más antiguos y sencillos. 

Consiste en reemplazar cada letra del mensaje original (texto plano) por otra letra, número o símbolo, siguiendo un sistema determinado.

Para desencriptar este tipo de textos, el descifrado de sustitución monoalfabética se basa en el **análisis de frecuencia y patrones comunes del lenguaje**.

Para esto utilizaremos una herramienta *Substitution Solver*, ingresaremos el texto dado y romperá este para encontrar una llave y mostrar el texto ya desencriptado.

```
-------------------------------------------------------------------------------
congrats here is your flag - frequency_is_c_over_lambda_agflcgtyue
-------------------------------------------------------------------------------
between us there was, as i have already said somewhere, the bond of the sea. besides holding our hearts together through long periods of separation, it had the effect of making us tolerant of each other's yarnsand even convictions. the lawyerthe best of old fellowshad, because of his many years and many virtues, the only cushion on deck, and was lying on the only rug. the accountant had brought out already a box of dominoes, and was toying architecturally with the bones. marlow sat cross-legged right aft, leaning against the mizzen-mast. he had sunken cheeks, a yellow complexion, a straight back, an ascetic aspect, and, with his arms dropped, the palms of hands outwards, resembled an idol. the director, satisfied the anchor had good hold, made his way aft and sat down amongst us. we exchanged a few words lazily. afterwards there was silence on board the yacht. for some reason or other we did not begin that game of dominoes. we felt meditative, and fit for nothing but placid staring. the day was ending in a serenity of still and exquisite brilliance. the water shone pacifically; the sky, without a speck, was a benign immensity of unstained light; the very mist on the essex marsh was like a gauzy and radiant fabric, hung from the wooded rises inland, and draping the low shores in diaphanous folds. only the gloom to the west, brooding over the upper reaches, became more sombre every minute, as if angered by the approach of the sun.

```

Dándonos así la bandera.

# **Notas adicionales**


# **Referencias**




