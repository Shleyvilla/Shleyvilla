importer  ftx
importer des  pandas  en tant que  pd
importer  ta
 temps d'importation
importer  json
de l'  import mathématique  * 

nom_compte  =  ''
pairSymbol  =  'BTC/USD'
fiatSymbol  =  'USD'
cryptoSymbol  =  'BTC'
maTronquer  =  4

client  =  ftx . FtxClient ( api_key = '' ,
                   api_secret = '' , subaccount_name = accountName )

données  =  client . get_historical_data (
    nom_marché = pairSymbol ,
    résolution = 3600 ,
    limite = 650 ,
    heure_début = flottant (
    rond ( temps . temps ())) - 650 * 3600 ,
    heure_de_fin = float ( rond ( heure . heure ())))
df  =  pd . DataFrame ( données )

df [ 'SMA200' ] =  ta . tendance . sma_indicator ( df [ 'fermer' ], 200 )
df [ 'SMA600' ] =  ta . tendance . sma_indicator ( df [ 'fermer' ], 600 )
impression ( df )

def getBalance(myclient, coin):
    jsonBalance  =  monclient . get_balances ()
    si  jsonBalance  == [] :
        retour  0
    pandaBalance  =  pd . DataFrame ( jsonBalance )
    imprimer ( pandaBalance )
    si  pandaBalance . loc [ pandaBalance [ 'pièce' ] ==  pièce ]. vide :
        retour  0
    sinon :
        return  float ( pandaBalance . loc [ pandaBalance [ 'pièce' ] ==  pièce ] [ 'total' ])

def  tronquer ( n , décimales = 0 ):
    r  =  plancher ( float ( n ) * 10 ** décimales ) / 10 ** décimales
    retour  chaîne ( r )
    

prixréel  =  df [ 'fermer' ]. iloc [ - 1 ]
fiatAmount  =  getBalance ( client , fiatSymbol )
cryptoAmount  =  getBalance ( client , cryptoSymbol )
print ( prixréel , fiatAmount , cryptoAmount )

si  float ( fiatAmount ) >  5  et  df [ 'SMA200' ]. iloc [ - 2 ] >  df [ 'SMA600' ]. iloc [ - 2 ] :
    quantitéBuy  =  truncate ( float ( fiatAmount ) / actualPrice , myTruncate )
    achatCommande  =  client . passer_commande (
        marché = paireSymbole ,
        côté = "acheter" ,
        prix = Aucun ,
        taille = quantitéAcheter ,
        type = 'marché' )
    imprimer ( acheterCommande )

elif  float ( cryptoAmount ) >  0.0001  et  df [ 'SMA200' ]. iloc [ - 2 ] <  df [ 'SMA600' ]. iloc [ - 2 ] :
    achatCommande  =  client . passer_commande (
        marché = paireSymbole ,
        côté = "vendre" ,
        prix = Aucun ,
        size = truncate ( cryptoAmount , myTruncate ),
        type = 'marché' )
    imprimer ( acheterCommande )
sinon :
  print ( "Aucune opportunité" )
