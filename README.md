# Proj-mathinfo1
Projet Maths/Info Laperrouze/Arguelle

Amorce : Si on pose g : t |--> f(0,t) définie sur [0;1]. Avec l'hypothèse de f continûment différentiable, on obtient que g est C1,
 Donc avec le théorème des valeurs intermédiaires appliquées à g, il semble raisonnable de fixer f(0;0)<c<f(0;1) pour être certain d'obtenir t appartenant à [0;1] tel que f(0;t)=c


def find_seed(g, c=0, eps=2**(-26)):
    
    y0=0
    
    while abs(g(O,y0))>eps:
        
        y0= y0 - (g(0,y0)/deriv(g,y0))
        
    return y0
    
