Análise técnica da execução

Sem sincronização de dados, temos desordem e muitos erros, com a sincronização com monitores, múltiplas threads são impedidas de serem criadas ao mesmo tempo, garante exclusão mútua, porém não há uma coordenação direta, e agora com a sincronização com eventos, conseguimos o equilibrio ideal, produtor e consumidor trabalham em harmonia, alternando corretamente o que garante resultados consistentes. 
