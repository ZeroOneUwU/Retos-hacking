## Descripcion 

Kishor Balan nos advirtió que el siguiente código podría necesitar inspección: https://jupiter.challenges.picoctf.org/problem/9670/ (link) o http://jupiter.challenges.picoctf.org:9670
## Solucion

entrar al link
inspeccionar codigo fuente

	  HTML <br/>
	  CSS <br/>
	  JS (JavaScript)
	</p>
	<!-- Html is neat. Anyways have 1/3 of the flag: picoCTF{tru3_d3 -->
      </div>
      
    </div>
    
  </body>
</html>


damos click a mycss.css
<link rel="stylesheet" type="text/css" href="mycss.css">


.tabcontent {
    color: #111;
    display: none;
    padding: 50px;
    text-align: center;
}

#tabintro { background-color: #ccc; }
#tababout { background-color: #ccc; }

/* You need CSS to make pretty pages. Here's part 2/3 of the flag: t3ct1ve_0r_ju5t */
window.onload = function() {
    openTab('tabintro', this, '#222');
}

/* Javascript sure is neat. Anyways part 3/3 of the flag: _lucky?2e7b23e3} */

picoCTF{tru3_d3t3ct1ve_0r_ju5t_lucky?2e7b23e3}


## Notas adicionales

