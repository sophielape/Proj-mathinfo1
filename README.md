# Proj-mathinfo1
Projet Maths/Info Laperrouze/Arguelle

Amorce : Si on pose g : t |--> f(0,t) définie sur [0;1]. Avec l'hypothèse de f continûment différentiable, on obtient que g est C1,
 Donc avec le théorème des valeurs intermédiaires appliquées à g, il semble raisonnable de fixer f(0;0)<c<f(0;1) pour être certain d'obtenir t appartenant à [0;1] tel que f(0;t)=c



    def find_seed(g, c=0, eps=2**(-26)):
     t=0
     
    max=max(g(0,1), g(0,0))
    min=min(g(0,1), g(0,0))
    
    if c>max or c<min:
        return None
    
     while abs(g(0,t)-c)>eps:
        
        t= t - (g(0,t)/deriv(g,t))
        
     return t
     
     
     
     
    def deriv2(g,x):
     h=10**(-10)
     a=g(0,x+h)-g(0,x-h)
     return a/(2*h)
    
