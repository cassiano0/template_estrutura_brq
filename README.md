### BOAS PRÁTICAS
- Faça um pull request.
- Estruture suas pastas de acordo com o padrão MVC.
- Comente seu código!


# POLÍTICA DE DESENVOLVIMENTO DE SOFTWARE GRUPOBRQ

## ESTRUTURA DE PASTAS
A hierarquia de pastas é clara e simples. Mantenha sempre organizada.

## PROTHEUS
Para localizar sua pasta exclusiva de desenvolvimento, acesse seu login e senha via guacamole.
Acesse:

B:\”PROTHEUS HML `EMPRESA`”\Protheus\”my projects”\\`nome.sobrenome`

Em seguida clone o repositório com o link GitHub fornecido.

## ALTERAÇÕES EM PARÂMETROS PROTHEUS
Mudanças em parâmetros do PROTHEUS devem ser deixados na sua pasta em um arquivo chamado `parâmetros.txt`

Neste arquivo coloque o nome do parâmetro alterado e utilize a expressão `--` para representar o rollback. Preencha um parâmetro por linha, conforme exemplo abaixo.

Exemplo:

`nome.sobrenome\parametros.txt`
```sql
-- MV_GRVBLQ2: F
MV_GRVBLQ2: T
```

## MUDANÇAS EM BANCO DE DADOS PROTHEUS
Toda e qualquer mudança no banco de dados deverá ser registrada para fins histórico.
Para isso, dentro da sua pasta crie uma subpasta DB e dentro dela deverão existir arquivos com o nome da tabela alterada.
Para fins de registro, utilize a query equivalente ao que foi feito no APSDU. E defina o rollback comentado.

Exemplo: 

`nome.sobrenome\DB\SA1.sql`
```sql
-- ALTER TABLE SA1030 ALTER COLUMN A1_LOJA VARCHAR(2)
ALTER TABLE SA1030 ALTER COLUMN A1_LOJA VARCHAR(3)

-- ALTER TABLE SA1040 ALTER COLUMN A1_LOJA VARCHAR(2)
ALTER TABLE SA1040 ALTER COLUMN A1_LOJA VARCHAR(3)

-- DROP TABLE IF EXISTS ZZEXEMPLO
CREATE TABLE ZZEXEMPLO (...
```

## AMBIENTES
Trabalharemos sempre em 3 ambientes, PRODUÇÃO, HOMOLOGAÇÃO e DESENVOLVIMENTO.
DESENVOLVIMENTO
Solicite seu acesso via guacamole. Neste ambiente, você terá uma branch com nome da sua empresa. Faça tudo que precisa e realize um PULL-REQUEST para HOMOLOG e informe para iniciar os testes.
Com os testes 100%, solicite um PULL-REQUEST do HOMOLOG para branch MAIN.

### GIT BRANCHES
•	MAIN: Fontes no ambiente de PRODUÇÃO. Faça a branch a partir desta com seu *nome.sobrenome* .

•	HOMOLOG: Branch para ambiente de HOMOLOGAÇÃO e testes por parte dos usuários chave, deverá ser acompanhado pelo desenvolvedor + analista GrupoBRQ. Após validado pelo usuário e funcionando, realize PULL-REQUEST para a branch MAIN. Não realize o merge direto na MAIN!

•	DEV: Branch local dos desenvolvedores. Somente nesta branch deverá ter código alterado. Assim que os códigos forem finalizados, realize PULL-REQUEST. Não realize o merge direto na HOMOLOG ou na MAIN.

#### PULL-REQUEST
O responsável pelo pull-request para branches HOMOLOG e MAIN sempre será o desenvolvedor e a aceitação e merge sempre será por um analista do GrupoBRQ.
Em caso de falha no MERGE o analista do GrupoBRQ deverá reunir os desenvolvedores e mediar as correções.
Para compreender melhor a funcionalidade do PULL-REQUEST veja esse vídeo tutorial do GitKraken: https://youtu.be/2VX1ISk9XH8
