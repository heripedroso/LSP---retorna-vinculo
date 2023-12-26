# LSP---retorna-vinculo
Função que retorna a descrição do vínculo.

## Função que retorna o vínculo de acordo com o teto informado no parâmetro de entrada.
Apesar de já haver a função nativa `RetVinEmp`, preferi utilizar um parâmetro de entrada numérica para interagir com a estrutura objColaborador. Creio que dessa forma seja mais interessante e elegante.

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
## Recomendações
Para usar a função na regra, deve-se declará-la no início da mesma.
É interessante que se reserve, por exemplo, a regra 001 apenas para implementar funções.

Em implementações de relatório, tenho o hábito de declarar as funções em `Funções Globais` no `Modelo Gerador`.

![image](https://github.com/heripedroso/LSP---converte-minutos-em-HH-MI/assets/22459829/fa6ef8f7-399d-4923-9c2e-a814f502bddc)
