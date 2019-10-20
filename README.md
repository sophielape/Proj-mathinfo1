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
        
        t= t - (g(0,t)/deriv(g,0, t))
        
     return t
     
 On choisit la méthode de Newton corrigée par c pour trouver le  de la fonction auxiliaire h=g-c. On obtient donc un 0 correspondant (ou pas).     
     
    def deriv2(g,x,y):
     h=10**(-10)
     a=g(x,y+h)-g(x,y-h)
     return a/(2*h)
     
Propagation : l'idée est de parcourir l'un des cotés de notre carré et de relever un point de la ligne de niveau à chaque "arret" sur ce coté, arrêts espacés de delta. Pour ceci, il nous faut modifier nos fonctions ci dessus pour se déplacer librement sur la première coordonnée de f sans rester bloqué sur 0. Pour respecter la proximité de delta au niveau de x et y, on initialise une première valeur de coordonnées de la ligne de niveau, puis on se place dans un intervalle autour de la première valeur de y au lieu de rester sur [0;1]. Ceci permet également de palier au problème rencontré si notre ligne de niveau fait un "lacet", ce qui engendrerait deux valeurs possibles de y pour un même x. Dans ce cas, nos tableaux n'auraient pas forcément présenté de continuité sur la ligne de niveau. 
    

    def simple_contour(f, c=0.0, delta=0.01):
    
    X=np.arange(0,1, delta
    y0=0
    Y=[y0]
    
    
    for x0 in X:
        y0=find_seed2(x0,y0, g)
        Y.append(y0)
        
    
    s=0
    Yfinal=[]
    
    while y0!= None and s<len(Y):
        Yfinal.append(y0)
        s=s+1
        y0=Y[s]

  
    return X[:len(Yfinal)],Yfinal
    
        
    
    def find_seed2(x, y ,g, c=0, eps=2**(-26), delta=0.01):
    
    max=max(g(x,y-delta), g(x,y+delta))
    min=min(g(x,y-delta), g(x,y+delta))
    
    if c>max or c<min:
        return None
    
    while abs(g(x,y))>eps:
        
        y= y - (g(x,y)/deriv(g,x,y))
        
    return y
