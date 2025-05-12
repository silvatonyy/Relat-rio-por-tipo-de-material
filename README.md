Relatório ABAP – Consulta de Descrições de Materiais

Este relatório tem como objetivo buscar descrições de materiais na tabela MAKT, com base nos materiais previamente selecionados da tabela MARA.
Utiliza o comando FOR ALL ENTRIES IN, que permite realizar uma seleção eficiente no banco de dados, trazendo apenas os registros de descrição (MAKT) correspondentes aos códigos de material (MATNR) já obtidos.
Além disso, o relatório filtra as descrições pelo idioma do usuário logado no sistema, usando o campo SY-LANGU.
Resumo técnico do SELECT:
SELECT *
  FROM makt
  INTO TABLE it_makt
  FOR ALL ENTRIES IN it_mara
  WHERE matnr = it_mara-matnr
    AND spras = sy-langu.

Utilização de FOR ALL ENTRIES para evitar múltiplos SELECTs dentro de loops.
Filtro por idioma (SY-LANGU) para garantir que o usuário visualize os textos na sua linguagem.
Importância de verificar se it_mara não está vazia antes de executar o SELECT, evitando consultas desnecessárias.
