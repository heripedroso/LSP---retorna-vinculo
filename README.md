# LSP---retorna-vinculo
Função que retorna a descrição do vínculo.

## Função que retorna o vínculo de acordo com o teto informado no parâmetro de entrada.
Apesar de já haver a função nativa RetVinEmp, preferi utilizar um parâmetro de entrada numérica para interagir com a estrutura objColaborador. Creio que dessa forma seja mais interessante e elegante.
```
Definir Funcao retornaVinculo(Numero nTeto);

Funcao retornaVinculo(Numero nTeto);
{
     nNumEmp = objColaborador[nTeto].nNumEmp;
     nTipCol = objColaborador[nTeto].nTipCol;
     nNumcad = objColaborador[nTeto].nNumCad;
     Definir Data dDataRef; dDataRef = objParamentrosEntrada[1].dDataFimDoMes;
     
     RetVinEmp(nNumEmp, nTipCol, nNumCad, dDataRef);
     xCodVinEmp = CodVinEmp;
     
     Definir Cursor cCurVinculo;
     cCurVinculo.SQL "select R022VIN.DesVin from R022VIN where CodVin = :xCodVinEmp";
     cCurVinculo.AbrirCursor();
     SE (cCurVinculo.Achou){ 
         objColaborador[nTeto].aVinculo = cCurVinculo.DesVin; 
     };
     cCurVinculo.FecharCursor();
};
```
