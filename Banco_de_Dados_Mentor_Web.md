# Documentação Banco de Dados Mentor Web

Neste documento não estão previstas informações comuns como profissões, religiões, raças, municípios, nacionalidades. Também não estão previstas informações acadêmicas como horários gerais, professores das disciplinas, crogramas de aula das turmas, avaliações parciais, faltas diárias, conteúdos ministrados, pré requisitos em grades curriculares, dados de monografia, estágio e atividades complementares.

- [Documentação Banco de Dados Mentor Web](#documentação-banco-de-dados-mentor-web)
  - [CAMPOS COMUNS A TODAS AS TABELAS:](#campos-comuns-a-todas-as-tabelas)
  - [TB\_PESSOA](#tb_pessoa)
  - [TB\_MUNICIPIO](#tb_municipio)
  - [TB\_UNIDADE\_FEDERACAO](#tb_unidade_federacao)
  - [TB\_DISCIPLINA](#tb_disciplina)
  - [TB\_PERIODO\_LETIVO](#tb_periodo_letivo)
  - [TB\_TURMA](#tb_turma)
  - [TB\_CURSO](#tb_curso)
  - [TB\_REGRA\_MATRICULA\_CURSO](#tb_regra_matricula_curso)
  - [TB\_TURMA\_DISCIP](#tb_turma_discip)
  - [TB\_PADRONIZACAO\_DIS](#tb_padronizacao_dis)
  - [TB\_PADDIS\_TIPNOT](#tb_paddis_tipnot)
  - [TB\_GRADE](#tb_grade)
  - [TB\_DISCIPLINA\_GRADE](#tb_disciplina_grade)
  - [TB\_INGRESSO](#tb_ingresso)
  - [TB\_MESTRE\_ALUNO](#tb_mestre_aluno)
  - [TB\_MESTRE\_DISCIPLINA](#tb_mestre_disciplina)
  - [TB\_MESTRE\_DISCIPLINA\_DISGRADE](#tb_mestre_disciplina_disgrade)
  - [TB\_HISTORICO](#tb_historico)
  - [TB\_RESULTADO\_FASE](#tb_resultado_fase)
  - [TB\_VALIDACAO](#tb_validacao)
  - [TB\_HISTORICO\_EXTERNO](#tb_historico_externo)
  - [TB\_AVAPAR\_CADAVA](#tb_avapar_cadava)
  - [TB\_AVAPAR\_REGNOT](#tb_avapar_regnot)
  - [TB\_SITUACAO\_RESULTADO](#tb_situacao_resultado)
  - [TB\_CRONOGRAMA\_AULA](#tb_cronograma_aula)
  - [TB\_CRONOGRAMA\_AULA\_DATA](#tb_cronograma_aula_data)
  - [TB\_CRONOGRAMA\_AULA\_PROF](#tb_cronograma_aula_prof)
  - [TB\_TURMADISCIP\_PROF](#tb_turmadiscip_prof)
  - [TB\_FORMACAO\_ACADEMICA\_PES](#tb_formacao_academica_pes)
  - [TB\_CONTRATO\_FIN](#tb_contrato_fin)
  - [TB\_RESPONSAVEL\_FIN](#tb_responsavel_fin)
  - [TB\_DESCONTO](#tb_desconto)
  - [TB\_RESPONSAVEL\_DESACR](#tb_responsavel_desacr)
  - [TB\_PARCELA](#tb_parcela)
  - [TB\_PARCELA\_DESACR](#tb_parcela_desacr)
  - [TB\_PARCELA\_PAG](#tb_parcela_pag)
  - [TB\_PARCELA\_PAG\_DESACR](#tb_parcela_pag_desacr)
  - [TB\_TITULO\_BANCARIO](#tb_titulo_bancario)
  - [TB\_REMESSA\_TITULO](#tb_remessa_titulo)


## CAMPOS COMUNS A TODAS AS TABELAS:

- GRUPO_UNIDON - id do grupo de unidade do registro
- UNIDON - id da unidade do registro
- DATA_ULT_ALTERACAO - data da ultima alteração do registro
- USUARIO_ULT_ALTERACAO - último usuário que alterou o registro
- VERSAO - quantidade de vezes que o registro foi alterado
- ATIVO - 1 para ativo e 0 para inativo

## TB_PESSOA
(tabela utilizada para qualquer tipo de pessoa... alunos, professores, responsáveis, pais, mães, funcionários, coordenadores e etc)

- PES_ID - PK AUTO INCREMENTADO
- PES_TIPPES - 1 para fisica 2 pra juridica
- PES_PEREMAIL - 1 para permite e-mail e 0 para não permite
- PES_PERSMS - 1 para permite sms e 0 para não permite
- PES_CODTEL - Código de matrícula do aluno. Este campo é único na base, então mesmo código em unidades diferentes não será permitido.
- PES_NOME - Nome do aluno. Não aceitará números, traços e pontos, nem outros caracteres especiais.
- PES_EMAIL - Exige uma @ e um .
- PES_ENDERE - Corre o risco de truncar. Permite 60 caracteres eu acho.
- PES_BAIRRO - Corre o risco de truncar. Permite 60 caracteres eu acho.
- PES_COMEND - Complemento de Endereço. Corre o risco de truncar. Permite 60 caracteres eu acho.
- PES_NUMERO - Número do endereço.
- PES_CEP - Cep do endereço da pessoa, sem "-".
- PES_CODMUN - id do cadastro de município do mentor. município de endereço.
* Replicar PES_ENDERECOB, PES_NUMEROCOB, PES_BAIRROCOB, PES_CODMUNCOB, PES_CEPCOB, PES_COMENDCOB conforme os campos acima a menos que haja dados de cobrança identificados.
- PES_DATNAS - Data de nascimento da pessoa.
- PES_NRODOC1 - CPF da pessoa. Deve possuir 11 caracteres sem " - " ou " . ".
- PES_NRODOC2 - Rg do aluno.
- PES_ESTCIV - Estado civil da pessoa. Sigla de enumeração. UEST = União Estável, C = Casado, S = Solteiro, D = Divorciado, V = Viúvo, J = Separação Judicial.
- PES_FONCEL - telefone celular da pessoa, padronizado com máscara
- PES_FONCOM - telefone comercial da pessoa, padronizado com máscara
- PES_FONE - telefone da pessoa, padronizado com máscara
- PES_TIPNAC - enumeração de tipo de nacionalidade do aluno. BRASIL / ESTRAN
- PES_MUNNASID - id do cadastro de município do mentor. município de nascimento.
- PES_OCPID - id do cadastro de ocupação profissional.
- PES_ORGEMIDOC2 - orgão emissor do rg
- PES_SEXO - Sexo da pessoa: M ou F
- PES_NROCERCIV - Número da certidão de nascimento ou casamento
- PES_EHALUNO - 1 para aluno 0 pra não aluno
- PES_CODINEP - código no inep do aluno
- PES_MAEID - id de cadastro de pessoa física que é mãe do aluno
- PES_PAIID - id de cadastro de pessoa física que é pai do aluno
- PES_RESPEDID - id de cadastro de pessoa física que é responsável pedagógico do aluno
- PES_RESFINID - id de cadastro de pessoa física que é responsável financeiro do aluno
- PES_DATDOC2 - data de emissão do rg
- PES_DATCERCIV - data de registro da certidão de nascimento / casamento.
- PES_FOLHACERCIV - folha de registro da certidão
- PES_LIVCERCIV - livro de registro da certidão

## TB_MUNICIPIO
(Cadastro de municípios)
- MUN_ID - id da pk auto incremento
- MUN_NOME - nome ou descrição do município
- MUN_UFID - id do cadastro de uf do município
- MUN_CEPINI - cep incial do município
- MUN_CEPFIN - cep final do município

## TB_UNIDADE_FEDERACAO
(Cadastro de unidades da federação)
- UFE_ID - id da pk auto incremento
- UFE_SIGUF - sigla da unidade de federação
- UFE_NOME - nome da unidade de federação
- UFE_PAISID - id do cadastro de país da uf

## TB_DISCIPLINA
(cadastro físico e atemporal da disciplina na base)
- DIS_DISID - id da pk auto incremento
- DIS_ABREVI - Abreviação da disciplina, utilizado em alguns relatórios.
- DIS_DESDIS - Descrição da disciplina
- DIS_DISTEL - código da disciplina.
- DIS_FORREA - enumerador do tipo de aula da disciplina: PR para presencial
- DIS_SNDID - id do cadastro de subnível de ensino da disciplina
- DIS_CHORTH - carga horária teórica

## TB_PERIODO_LETIVO
(cadastro dos períodos letivos)
- PEL_PERID - id da pk auto incremento
- PEL_DESCRI - Descrição que aparece em tela do período letivo
- PEL_SEQUENCIA - Sequencial simples. Importante, pois a ordenação em tela obedece este campo de maior pra menor.
- PEL_DATINI - Data inicial do período letivo. É sugerida em alguns cadastros e processos, portanto, útil
- PEL_DATFIN - Data final do período letivo. É sugerida em alguns cadastros e processos, portanto, útil
- PEL_SNCID - id do cadastro de subnível de ensino do período letivo
- PEL_ANOREF - Ano de referência, usado para algumas questões importantes como relatórios.
- PEL_SEMESTRE - Semestre do período letivo.

## TB_TURMA
(cadastro das turmas ofertadas e temporais - conforme período letivo - na base)
- TUR_ID - id da pk auto incremento
- TUR_CODTUR - código de tela da turma. utilizado nas rotinas do sistema.
- TUR_PERID - id do cadastro de período letivo desta turma.
- TUR_PDIID - id do cadastro de critério de avaliação por disciplina desta turma.
- TUR_PADID - id do cadastro de critério de avaliação por turma desta turma. Normalmente é um geral.
- TUR_CURID - id do cadastro de curso desta turma.
- TUR_DATFIN - Data final da turma.
- TUR_DATINI - Data inicial da turma.
- TUR_DESCRI - Descrição da turma. Nome apresentável para relatórios.
- TUR_FASE - Fase da turma. Deve estar dentro do intervalo do seu curso ou da sua grade, se tiver.
- TUR_TURNO - Turno da turma: 'VeN' para Vespertino e Noturno, 'MeN' para Matutino e Noturno, 'MeV' para Matutino e Vespertino, 'M' para Matutino, 'V' para Vespertino, 'N' para Noturno, 'I' para Integral, 'ND' para Não definido.

- TUR_STATUS - situação da turma. Colocar 'ANDA' para turmas em andamento e 'CONC' para turmas concluídas. Se houver turma em inscrição, pode usar 'INSC'
- TUR_SEQTUR - sequencial de turma, obrigatório mas quase sem utilidade.
- TUR_SNCID - id do cadastro de subnível de ensino da turma.
- TUR_GRAID - id do cadastro de grade curricular desta turma. Deve ser informado apenas quando formato do curso é por grade curricular.
- TUR_TIPREG - regime de aulas da turma, padrão 'NORM'.
- TUR_RESACAID - id do cadastro de pessoa do coordenador da turma.

## TB_CURSO
(cadastro físico e atemporal dos cursos na base)
- CUR_ID - id da pk auto incremento
- CUR_NOMCUR - Nome do curso
- CUR_CODCUR - Código do curso
- CUR_SNDID - id do cadastro de subnível de ensino do curso.
- CUR_TIPDIS - Formato do curso: 'DTU' para cursos em disciplinas por turma e 'DGC' para cursos em disciplinas por grade curricular.
- CUR_NUMPER - Quantidade de fases do curso. Campo obrigatório e informado somente quando formato é por turma.
- CUR_NOMFAS - Nomenclatura das fases. Informação que sai em relatório. 'ANO', 'ETAPA', 'FASE', 'MODULO', 'PERIODO', 'SERIE'. Exemplo: 1º Ano ou 1ª Série.
- CUR_NROLIS - Número de lista dos alunos é definido por turma ou por disciplina nas turmas do curso. 'DIS' OU 'TUR'. Se quiser digitar faltas por dia precisa ser formato 'TUR'
- CUR_TIPOPER - sempre 'FASE'.
- CUR_ALUDEP - Alunos em dependência na turma devem ser 'CONNOR', Considerar normal ou 'ULTLIS', Último da lista.
- CUR_TCUID - id do cadastro do tipo de curso deste curso.

## TB_REGRA_MATRICULA_CURSO
(vínculo do curso com sua regra de matrícula)
- RGC_ID - id da pk auto incremento.
- RGC_CURID - id do cadastro de curso da tabela.
- RGC_RGMID - id do cadastro de regra de matrícula da tabela.

## TB_TURMA_DISCIP
(vínculo entre turmas e disciplinas. São as disciplinas ofertadas na turma)
- TDI_TURDISID - id da pk auto incremento.
- TDI_CHORTH - carga horária da disciplina ofertada
- TDI_PDIID - critério de avaliação por disciplina da disciplina ofertada
- TDI_DISCID - id do cadastro de disciplina da disciplina ofertada
- TDI_SEXO - sexo aceito na disciplina ofertada. 'AMBOS' para todos, 'M' para somente masculino e 'F' para somente feminino.
- TDI_SNCID - id do cadastro do tipo de curso desta disciplina ofertada.
- TDI_UTI_SUBTURMA - se a disciplina ofertada possui ou não subturmas. 'NAO' OU 'SIM'
- TDI_TDGID - id do cadastro de tipo de disciplina da disciplina ofertada.
- TDI_PLAENSAPR - indicação se o plano de ensino da disciplina ofertada está aprovado. Sempre '0'
- TDI_REPDIS - se a disciplina ofertada reprova ou não. '0' para não e '1' para sim.
- TDI_TIPDISCOMP - se a disciplina ofertada é agregadora agregada ou normal. 'N' para normal.
- TDI_TIPREG - Regime de aulas da disciplina ofertada. 'NORM' para normal ou semanal, 'ESPE' para especial, 'QUIN' para quinzenal e 'CONC' para concentrado.
- TDI_TURID - id do cadastro de turma da disciplina ofertada.
- TDI_CALMED - se a disciplina ofertada calcula média ou não. '0' para não e '1' para sim.
- TDI_MAXVAG - Máximo de vagas permitido na disciplina

## TB_PADRONIZACAO_DIS
(critério de avaliação vinculado a disciplina ofertada e a turma)	
- PDI_ID - id da pk auto incremento.
- PDI_DESCRI - Descrição do critério de avaliação
- PDI_DIGNOT - Formato da digitação de notas
- PDI_DIGAVAPAR - Formato de lançamento de avaliações parciais: PADPRO = Definido pelo professor, NAODIG = Não utiliza
avaliações parciais, PADINS = Definido pela instituição.

## TB_PADDIS_TIPNOT
(Avaliações ou Períodos do critério de avaliação)
- TNP_ID - id da pk auto incremento.
- TNP_PDIID - id do cadastro de critério de avaliação desta avaliação/período de critério.
- TNP_CODNOT - Código da avaliação/período
- TNP_DESCRI - Descrição da avaliação/período
- TNP_NOTCAL - Indica se é uma nota calculada. (uma média) 1 para sim, 0 para não.
- TNP_NOTEXA - Indica se é um exame. 1 para sim, 0 para não.
- TNP_ORDEM - Ordem de realização da avaliação/período
- TNP_NOTMINAPR - Nota mínima para aprovação. Somente para o tipo média.

## TB_GRADE
(cadastro físico e atemporal - porém renovável quando convém a instituição - de grades curriculares do curso na base) *somente cursos que utilizam grade necessitam deste cadastro.
- GRA_ID - id da pk auto incremento.
- GRA_CODGRA - código da grade curricular
- GRA_DESGRA - descrição da grade curricular
- GRA_CURID - id do cadastro de curso da grade
- GRA_VALINI - validade inicial da grade
- GRA_VALFIN - validade final da grade. Informar, quando uma grade já não é mais disponiblizada.
- GRA_CAHORH - carga horária total da grade. Validações são feitas a partir dessa informação.
- GRA_SNCID - id do cadastro de subnível de ensino da grade
- GRA_CARHORMINATICOM - Carga horária exigida para atividades complementares.
- GRA_POSSUIMOD - Indicador se a grade possui módulos ou não. '0' para não e '1' para sim.
- GRA_PEREXTJUB - Períodos que podem ser solicitados para prorrogar jubilamento
- GRA_PERLETJUBPORVEZ - Períodos que podem ser solicitados por solicitação para prorrogar jubilamento

## TB_DISCIPLINA_GRADE
(vínculo das disciplinas com a grade curricular. É atemporal, é chamado de componente curricular e somente em instituições de cursos com grade, se preenche esta tabela)
- DGR_ID - id da pk auto incremento.
- DGR_GRAID - id do cadastro de grade deste componente curricular.
- DGR_DISID - id do cadastro de disciplina deste componente curricular.
- DGR_FASDIS - fase deste componente curricular.
- DGR_ORDEM - ordem que será apresentado o componente curricular em listagens de matrícula e etc.
- DGR_REPDIS - indicador se este componente curricular reprova ou não. '1' para sim e '0' para não.
- DGR_SNCID - id do cadastro de subnível de ensino do componente curricular.
- DGR_TDGID - id do tipo de componente curricular deste componente curricular.

## TB_INGRESSO
(Vínculo formal, atemporal - porém renovável -  do aluno com o curso. Se torna renovável à medida que um aluno cancela, se transfere, abandona e em outro momento retoma o mesmo curso, aonde cria-se outro ingresso. Não sendo isso, mantém-se sempre o mesmo ingresso.)
- ING_ID - id da pk auto incremento.
- ING_CURID - id do cadastro de curso do ingresso.
- ING_DATENT - data de ingresso no curso.
- ING_PESID - id do cadastro de pessoa física do ingresso.
- ING_OBSERV - campo destinado a registrar de forma concatenada, todas as observações do ingresso do aluno. Muitas vezes o camapo é utilizado para imprimir informações no histórico.
- ING_STADIP - 'NAOEMI' valor padrão.
- ING_SNCID - id do cadastro de subnível de ensino do ingresso.
- ING_FINID - id do cadastro de forma de ingresso do ingresso.
- ING_APTMAT - indicação de aluno apto a se matricular ou não. '1' para sim e '0' para não.
- ING_STATUS - indicação da situação de ingresso do aluno. 'ATIVO' para alunos ativos, 'PREMAT' para alunos com a PRIMEIRA matrícula em situação de pré matrícula 'CANCEL' para alunos cancelados, 'CONCLUIDO' para alunos concluídos, 'DESIST' para alunos em abandono, 'DESLIG' para alunos desligados da instituição, 'JUBILADO' para alunos com o ingresso jubilado, 'TRACUR' para alunos com transferência de curso, 'TRAEXT' para alunos em transferência externa.
- ING_APTCOL - indicação de aluno apto a colar grau ou não. '1' para sim e '0' para não.
- ING_TURNO - turno do ingresso. 'VeN' para Vespertino e Noturno, 'MeN' para Matutino e Noturno, 'MeV' para Matutino e Vespertino, 'M' para Matutino, 'V' para Vespertino, 'N' para Noturno, 'I' para Integral, 'ND' para Não definido.
- ING_MALID - id do último mestre_aluno deste ingresso. Este campo deve ser atualizado via update somente após serem criados os mestre_alunos.
- ING_GRAID - id da grade curricular ao qual este ingresso pertence.
- ING_DATSAI - data de saída do ingresso. Obrigatório e apenas possível informar, quando situação do ingresso não é ativa nem pré matrícula.

## TB_MESTRE_ALUNO
(Vínculo formal, temporal do ingresso (e seu aluno com uma turma (e seu período letivo) - Em outras palavras é a matrícula de forma geral.))
- MAL_ID - id da pk auto incremento.
- MAL_INGID - id do cadastro de ingresso da matrícula.
- MAL_TURID - id do cadastro de turma da matrícula.
- MAL_DATENT - data de pré-matrícula.
- MAL_DATMAT - data de efetivação da matrícula.
- MAL_DATSAI - data de saída da matrícula. Necessário e informável, apenas quando situção de matrícula seja diferente de 'ATIVO' e 'PREMAT'.
- MAL_SITMAT - Situação da matrícula: 'AFAST, para aluno afastado, 'ATIVO', para aluno ativo, 'CANCEL', para aluno cancelado, 'DESIST', para aluno desistente ou em abandono, 'PREMAT', para aluno em pré matrícula, 'RECLAS', para aluno para aluno que foi reclassificado, 'REMANE',  para aluno remanejado de turma, 'SUSPE', para aluno com a matrícula suspensa, 'TRAEXT',  para aluno transferido, 'TRAINT', para aluno que mudou de curso na instituição, 'TRANCA'  para aluno que trancou a matrícula.
- MAL_SNCID - id do cadastro de subnível de ensino da matrícula.
- MAL_FASE - fase principal da matrícula.
- MAL_RESID - id do cadastro de situação de resultado da matrícula.
- MAL_PERFRE - percentual de frequência geral do aluno.
- MAL_CFIID - id do cadastro de contrato financeiro da matrícula.

## TB_MESTRE_DISCIPLINA
(Vínculo do mestre_aluno com as disciplinas, ou em termos gerais são as disciplinas da matrícula.)
- MDI_ID - id da pk auto incremento.
- MDI_TURDISID - id da disciplina ofertada desta disciplina matriculada.
- MDI_MALID - id da matrícula principal desta disciplina matriculada
- MDI_RESID - id do cadastro de situação de resultado desta disciplina matriculada
- MDI_TIPMAT - indica o tipo de matrícula na disciplina. 'ADA' indica matrícula em regime de adaptação, 'DEPFRE' para dependência por frequência, 'DEPNOT' para depend~encia por nota, 'DIS' para dispensado, 'ISOL' para disciplina isolada e 'NOR' para normal, o valor padrão.
- MDI_DATENT - data que o aluno foi matriculado na disciplina.
- MDI_DATSAI - data que o aluno saiu da disciplina por cancelamento, trancamento, remanejamento e afins.
- MDI_SITMAT - indica a situação de matrícula do aluno na disciplina. 'ATIVO' para matrícula ativa, 'CANCEL' para cancelada, 'PREMAT' para matrícula em situação de pré-matrícula, 'REMANE' para matrícula remanejada e 'TRANCA' para matrícula trancada.
- MDI_SNCID - id do cadastro de subnível de ensino desta disciplina matriculada.
- MD_PERFRE - assim sem o I, este campo indica o percentual de frequência do aluno na disciplina.
- MDI_MEDFIN - indica a média final do aluno na disciplina.
- MDI_NOTEXI - indica a nota de média final para exibição em documentos, do aluno na disciplina.
- MDI_DATHORCRIACAO - Data de criação do registro.
- MDI_IMPHIS - indica se a disciplina deve ser apresentada no histórico. 1 para sim e 0 para não.
- MDI_CHORT
- MDI_CHORP

## TB_MESTRE_DISCIPLINA_DISGRADE
(vínculo entre as disciplinas da grade do aluno com as disciplinas que o aluno está matrículado. É necessário apenas quando o curso trabalha com grade curricular).
- MDG_ID - id da pk auto incremento.
- MDG_DGRID - id da disciplina da grade.
- MDG_MDIID - id da disciplina matriculada.

## TB_HISTORICO
(Local onde estarão os registros de notas e faltas dos alunos. A granularidade desta tabela é: Nota e falta para cada avaliação do critério de avaliação definido para a disciplina que o aluno está matriculado.)
- HIS_ID - id da pk auto incremento.
- HIS_MDIID - id da disciplina matriculada.
- HIS_TNPID - id da avaliação do critério de avaliação
- HIS_NOTA - nota recebida/calculada pelo aluno
- HIS_FALTA - quantidade de faltas do aluno
- HIS_NOTEXI - nota apresentável em relatórios e tela.
- HIS_SNCID - id do cadastro de subnível de ensino deste registro de histórico.

## TB_RESULTADO_FASE
(É o resultado final do aluno na fase, ou série que o aluno estuda. Normalmente atribuído à educação básica seriada. Somente será necessário popular esta tabela se a regra de matrícula do curso trabalha por regime seriado, no qual controla-se o avanço de fase.)
- REF_ID - id da pk auto incremento.
- REF_INGID - id do ingresso do aluno ao qual o resultado da fase cursada foi atribuído.
- REF_RESID - id da situação de resultado obtida pelo aluno na fase e período atribuídos.
- REF_FASE - Fase (numérica) ao qual o resultado foi atribuído.
- REF_PERID - id do cadastro de período letivo em que o aluno obteve o resultado.

## TB_VALIDACAO
(Nesta tabela são lançadas as disciplinas ou fases curriculares que estão validadas. Estas validações podem ter vindo de outros cursos do colégio ou de outros colégio no caso de Ensino técnico ou superior ou de outros colégios na Educação básica. É possível lançar também os registros de Educação básica do próprio colégio para não lançar isso como matrículas, disciplinas da matrícula e históricos.)
- VAL_ID - id da pk auto incremento.
- VAL_INGID - id do ingresso do aluno da validação.
- VAL_DISID - id da disciplina validada nesta validação. Quando a validação é por fase, não é necessário informar este campo.
- VAL_FASDIS - id da fase cursada neste registro de validação. Ou será a fase da disciplina na grade ou no curso, quando se faz a validação do tipo disciplina ou a fase geral no qual se está fazendo a validação do tipo fase.
- VAL_LEGEND - Este campo só é preenchido quando o tipo de aprovação da validação é 'DIS'. Representa a legenda que representa a nota tirada.
- VAL_NOTA - Este campo só é preenchido quando o tipo de aprovação da validação é 'DIS'. Informação da nota da disciplina validada.
- VAL_FREQUE - Este campo só é preenchido quando o tipo de aprovação da validação é 'DIS'. Informação da frequência da disciplina validada.
- VAL_OBSERV - Campo de observação.
- VAL_SNCID - id do cadastro de subnível de ensino da validação.
- VAL_TIPAPR - indica se a validação realizada é por disciplina ou por fase. 'DIS' é utilizado para validar disciplinas individualmente e 'FASE' é utilizado para criar um registro de fase validada. Neste caso no histórico externo estarão vinculadas com esta validação as disciplinas cursadas na fase.
- VAL_SRDID - id do cadastro de situação de resultado da disciplina ou da fase validada.
- VAL_TIPVAL - tipo de validação. Pode usar por padrão 'TRAEXT'
- VAL_TIPDIS - tipo da disciplina validada. Pode usar por padrão 'DISCUR'
- VAL_PELID - id do período letivo em que a validação é lançada.

## TB_HISTORICO_EXTERNO
(Nesta tabela estão os dados da disciplina cursada na sua origem - outro curso ou outra instituição de ensino -. Pode estar vinculada a uma disciplina da validação ou a uma fase da validação.)
- HIE_ID - id da pk auto incremento.
- HIE_NOMDIS - Descrição da disciplina cursada externamente.
- HIE_FASDIS - Descrição da fase cursada externamente.
- HIE_NOMCUR - Descrição do curso cursado externamente.
- HIE_PESID - id de pessoa jurídica que indica a instituição na qual a disciplina foi cursada
- HIE_DISID - id do cadastro de disciplina do histórico externo. Essa informação deve ser preenchida quando eu quero que a disciplina saia no histórico. A fase de qualquer forma vai estar validada com ou sem o histórico externo. Quando o tipo de aprovação da validação é 'DIS', essa informação não é necessária.
- HIE_NOTA - nota recebida na disciplina cursada externamente.
- HIE_FREQUE - frequência recebida na disciplina cursada externamente.
- HIE_CHORTH - carga horária da disciplina cursada externamente.
- HIE_PERIODO - Ano letivo em que a disciplina foi cursada externamente.
- HIE_VALID - id do registro de validação ao qual pertence este registro de histórico externo.
- HIE_SNCID - id do cadastro de subnível de ensino do histórico externo.
- HIE_TDGID - id do cadastro de tipo de componente curricular da disciplina cursada externamente.
- HIE_PROF
- HIE_TIT

## TB_AVAPAR_CADAVA
(Nesta tabela estão contidas as avaliações parciais, provas, trabalhos e outros, cadastrados pelo professor ou pela instituição para a disciplina da turma.)
- APC_ID - id da pk auto incremento.
- APC_DESCRI - Descrição da avaliação parcial.
- APC_SIGLA - Sigla da avaliação parcial.
- APC_TDIID - Id da disciplina da turma ao qual a avaliação parcial foi cadastrada.
- APC_TNPID - Nota/período geral (bimestre por exemplo) ao qual a avaliação foi cadastrada.
- APC_PESO - Peso da avaliação.
- APC_CONTEUDO - Conteúdo da avaliação.

## TB_AVAPAR_REGNOT
(Registro de nota em avaliação parcial a identificação do aluno se baseia no relacionamento entre a pessoa física > seu ingresso > seu mestre_aluno > seu mestre_disciplina > seu histórico).
- APR_ID - id da pk auto incremento.
- APR_APCID - id da avaliação parcial ao qual esta nota de avaliação parcial foi atribuída.
- APR_HISID - id do histórico (aluno indiretamente) ao qual esta nota foi atribuída.
- APR_NOTA - Nota (formato de cálculo) informada pelo professor.
- APR_NOTEXI - Nota (formato de exibição em tela) informada pelo professor.

## TB_SITUACAO_RESULTADO
(Tabela de situações de resultado possíveis em disciplina cadastradas no sistema)
- SRD_ID - id da pk auto incremento.
- SRD_DESABV - Descrição abreviada da situação de resultado.
- SRD_DESRES - Descrição da situação de resultado.
- SRD_CODAPR - Tipo fixo da situação (APR = Aprovado - CUR = Cursando - DES = Desistente - DIS = Dispensado - EXA = Em exame - NCO = Não concluiu - REC = Reclassificado - RFR = Reprovado por frequência - RME = Reprovado por média)

## TB_CRONOGRAMA_AULA
(Contém nesta tabela cada horário de aula da disciplina ofertada na turma)
- CAU_ID - id da pk auto incremento.
- CAU_CADID - id da data de aula deste horário de aula.
- CAU_HORID - id do cadastro de faixa de horário desta aula.
- CAU_SALIID - id do cadastro de ambiente físico.
- CAU_TIPAUL - Tipo de aula deste horário. (TEORICA/PRATICA).

## TB_CRONOGRAMA_AULA_DATA
(Contém nesta tabela cada data de aula da disciplina ofertada na turma)
- CAD_ID - id da pk auto incremento.
- CAD_TDIID - id da disciplina da turma ao qual a data da aula foi atribuída.
- CAD_DATA - Data da aula.
- CAD_DIASEM - Dia da semana (1 a 7).
- CAD_DATADIGITADA - Caso preenchida, indica que a frequência já foi digitada para esta data, nesta disciplina da turma.

## TB_CRONOGRAMA_AULA_PROF
(Contém nesta tabela o professor atribuído de cada horário de aula da disciplina ofertada na turma)
- CAP_ID - id da pk auto incremento.
- CAP_CAUID - id do horário de aula ao qual este horário do professor representa.
- CAP_PESID - id do cadastro de pessoa do professor.
- CAU_HORCOM - Indica se o horário para o professor é compartilhado ou não (0/1).
- CAU_HORCON - Indica se o horário para o professor está confirmado ou não (0/1).

## TB_TURMADISCIP_PROF
(Professores vinculados à disciplina ofertada na turma, via inclusão em cronograma ou manualmente)
- TDP_ID - id da pk auto incremento.
- TDP_TDIID - id da disciplina da turma ao qual o professor foi vinculado.
- TDP_PESID - id do cadastro de pessoa do professor.

## TB_FORMACAO_ACADEMICA_PES
(Formação acadêmica da pessoa)
- FAP_ID - id da pk auto incremento
- FAP_PESID - id da pessoa física que possui a formação
- FAP_FOAID - id do cadastro do tipo de formação acadêmica
- FAP_DATINI - Data inicial da formação
- FAP_DATCON - Data final da formação
- FAP_CURSO - Curso da formação
- FAP_STATUS - Status da formação: A = Andamento, C = Concluído, D = Desistente
- FAP_ESTENSID - id da pessoa jurídica que representa a instituição de ensino em que a formação foi realizada
- FAP_ANOCON - Ano de conclusão da formação

## TB_CONTRATO_FIN
(Vínculo paralelo ao mestre_aluno, porém deve ser criado antes, pois é necessário para popular os mestre_alunos. A diferença entre eles é que o contrato financeiro possui dados financeiros e não acadêmicos. Como são paralelos estão no mesmo nível de detalhe, para cada turma/período letivo haverá 1 pra 1 mestre_aluno e contrato_fin. Mesmo que a instituição não possua financeiro, é necessário criá-los.)
- CFI_ID - id da pk auto incremento.
- CFI_PESID - id do cadastro de pessoa física do contrato
- CFI_DESCRI - descrição do contrato financeiro. É interessante conter ao menos o nome do aluno, sua turma e o período letivo na descrição.
- CFI_CURID - id do cadastro de curso do contrato financeiro.
- CFI_PERID - id do cadastro de período letivo do contrato financeiro.
- CFI_TURID - id do cadastro de turma do contrato financeiro.
- CFI_DIAVCT - Dia mensal de vencimento preferencial do aluno, que será considerado na geração das parcelas, substituindo a data padrão prevista no plano de pagamento, caso o plano de pagamento permita o vencimento especial do aluno.

## TB_RESPONSAVEL_FIN
(Determina quais são os responsáveis financeiros do contrato financeiro do aluno. Necessita ao menos um, quando instituição possui financeiro.)
- RFI_ID - id da pk auto incremento.
- RFI_PESID - id do cadastro de pessoa que é um dos responsáveis do contrato. Normalmente vai ser o responsável financeiro vinculado ao cadastro de pessoa física que é o portador do contrato.
- RFI_CFIID - id do cadastro de contrato financeiro.
- RFI_PERPAG - percentual que este responsável paga. A soma dos percentuais responsáveis de um mesmo contrato deve chegar a 100%.
- RFI_PERPAGTAX - percentual que este responsável paga de taxas. A soma dos percentuais responsáveis de um mesmo contrato deve chegar a 100%.

## TB_DESCONTO
(Cadastro dos descontos a aplicar)	
- DES_ID - id da pk auto incremento.
- DES_DESCRI - Descrição do desconto
- DES_VALDES - Validade do desconto. Sem limite, até o vencimento e etc.
- DES_NRODIAS - Quando a validade é até um determinado dia, a informação do dia ou dos dias é preenchida neste campo.
- DES_TDEID - id do cadastro de tipo de desconto deste desconto
- DES_PERCEN - Percentual sugerido do desconto
- DES_VALOR - Valor financeiro sugerido do desconto

## TB_RESPONSAVEL_DESACR
(Determina para cada responsável/contrato, quais são seus descontos, se houver.)
- PDA_ID - id da pk auto incremento.
- PDA_RFIID - id do responsavel_fin do desconto/acréscimo de responsável.
- PDA_DESID - id do cadastro de desconto do desconto/acréscimo de responsável.
- PDA_ACRID - id do cadastro de acréscimo do desconto/acréscimo de responsável.
- PDA_ORDEM - ordem de aplicação do desconto de responsável.
- PDA_PERCEN - percentual a ser aplicado do desconto/acréscimo de responsável.
- PDA_VALOR - valor financeiro a ser aplicado do desconto/acréscimo de responsável.
- PDA_VALDE - validade inicial para aplicação do desconto/acréscimo de responsável.
- PDA_VALATE - validade final para aplicação do desconto/acréscimo de responsável.
- PDA_TIPDES - indicação da aplicação do desconto/acrésimo sobre. 'VALBRU' aplicará o desconto/acrésimo sobre o valor bruto da parcela e 'RESPON' aplicará sobre o valor calculado após o desconto/acréscimo de ordem selecionada ser aplicado.
- PDA_APLORD - quando o desconto/acréscimo é aplicado sobre o valor calculado após outro desconto/acréscimo, neste campo se indica a ordem deste outro desconto.

## TB_PARCELA
(Parcelas do contrato, e consequentemente de um aluno e de um responsável.)
- PAR_ID - id da pk auto incremento.
- PAR_CFIID - id do contrato financeiro ao qual a parcela pertence.
- PAR_VALBRU - valor bruto da parcela.
- PAR_CODPAR - código da parcela.
- PAR_RESPESID - id do cadastro de pessoa que é a responsável pela parcela.
- PAR_TDBID - id do cadastro de conta financeira da parcela.
- PAR_ACRSLIMGER - total de acréscimos de geração da parcela.
- PAR_ACRSLIMUTI - valor já utilizado de acréscimos de geração.
- PAR_ACRPAG - valor já utilizado de acréscimo de baixa.
- PAR_DESCLINUNI - indica se possui desconto com limite não único. '1' para sim e '0' para não
- PAR_DESCLIUNI - indica se possui desconto com limite único. '1' para sim e '0' para não
- PAR_DESSLIMGER - total de descontos de geração sem limite da parcela.
- PAR_DESSLIMUTI - valor já utilizado de descontos de geração sem limite.
- PAR_DATGER - data de geração da parcela.
- PAR_DATVCT - data de vencimento da parcela.
- PAR_SITPAG - situação de pagamento 1 = Em aberto - 2 = Parcialmente paga - 3 = Paga	
- PAR_VALPAG - somatório do valor de todos os pagamentos realizados na parcela.
- PAR_PERRESP - Percentual que o responsável paga da parcela. Caso seja 100% não necessita informar.
- PAR_PLPID - id do cadastro de plano de pagamento da parcela. Normalmente se cria um plano de pagamento padrão para a migração.
- PAR_TITID - id do título bancário vinculado à parcela.
- PAR_ULTDATPAG - data em que o último pagamento foi realizado na parcela.
- PAR_NRODOC -
- PAR_DATCAN -

## TB_PARCELA_DESACR
(Descontos vinculados à parcela.)
- PDA_ID - id da pk auto incremento.
- PDA_PARID - id da parcela ao qual este desconto de parcela está vinculado.
- PDA_DESID - id do cadastro de desconto ao qual se refere este desconto de parcela.
- PDA_ACRID - id do cadastro de acréscimo ao qual se refere este desconto de parcela.
- PDA_VALOR - valor do desconto APLICADO. Se a informação de origem é percentual, deve ser convertido.
- PDA_DATVAL - data de validade do desconto para ser CONCEDIDO. Campo informado somente em descontos com pontualidade.
- PDA_TDEID - quando desconto de parcela é um DESCONTO, informa-se neste campo o id do cadastro de tipo de desconto.
- PDA_TARID - quando desconto de parcela é um ACRÉSCIMO, informa-se neste campo o id do cadastro de tipo de acréscimo.
- PDA_DESUNI - indicador de desconto único ou não. Informação válida apenas para DESCONTOS. '1' para único e '0' para não único.
- PDA_VALAPL - valor de desconto já concedido do total aplicado deste desconto/acréscimo.
- PDA_ORDEM - ordem de aplicação do desconto. quando só há um, a ordem será 1.

## TB_PARCELA_PAG
(Pagamentos vinculados à parcela. Os pagamentos no mentor são separados e não agrupados.)
- PPA_ID - id da pk auto incremento.
- PPA_PARID - id da parcela ao qual este pagamento está vinculado.
- PPA_DATPAG - data em que este pagamento foi realizado.
- PPA_DATA_BAIXA - data em que a baixa da parcela foi realizada.
- PPA_DATCRE - data em que o pagamento realizado foi creditado.
- PPA_VALPAG - Valor do pagamento. Embuti juros, multa, acréscimos e descontos tanto de geração quanto de baixa.
- PPA_JURPAG - valor pago de juros.
- PPA_MULPAG - valor pago de multa.
- PPA_VALDES - valor de desconto de baixa (concedido na hora do pagamento) concedido no pagamento.
- PPA_VALACR - valor de acréscimo de baixa (cobrado na hora do pagamento) cobrado no pagamento.
- PPA_TBAID - id do cadastro do tipo de baixa utilizado neste pagamento.

## TB_PARCELA_PAG_DESACR
(Descontos concedidos , vinculados ao pagamento da parcela.)
- PPD_ID - id da pk auto incremento.
- PPD_PPAID - id do pagamento ao qual este desconto concedido em pagamento está vinculado.
- PPD_ACRID - id do cadastro de acréscimo ao qual se refere este acréscimo cobrado em pagamento.
- PPD_DESID - id do cadastro de desconto ao qual se refere este desconto concedido em pagamento.
- PPD_VALOR - valor do desconto ou acrécimo que foi concedido no pagamento realizado.

## TB_TITULO_BANCARIO
(Títulos bancários vinculados à parcela. É importante ressaltar que os títulos migrados apenas podem ser baixados. Processos como alteração, prorrogação e reimpressão não funcionam.)
- TIT_ID - id da pk auto incremento.
- TIT_NOSNUM - nosso número do título.
- TIT_NOSNUMDV - passar fixo 'ID'.
- TIT_NRODOC - Número do título. Deve ser único na base.
- TIT_SEUNUM - passar o número do título.
- TIT_SEQTIT - passar o número do título.
- TIT_LINDIG - passar fixo 'Incluido depois'
- TIT_PBOID - id do cadastro de modelo de boleto utilizado. Pode referenciar qualquer um já cadastrado.
- TIT_CBCID - id da conta bancária carteira vinculada a este título. Precisa criar a conta bancária, depois a carteira de cobrança, para então pesquisar no banco qual o id da conta bancária carteira a utilizar.
- TIT_VALTIT - valor principal do título.
- TIT_DATVCT - vencimento do título.
- TIT_DATVAL - passar fixo um campo no formato datetime com '31/12/2050'.
- TIT_PESID - id do cadastro de pessoa que é o pagador do título.
- TIT_SACADO - nome por extenso do pagador do título.
- TIT_BANCO - código nacional do banco do título.
- TIT_BANCODV - passar fixo 'ID'.
- TIT_AGENCIA - agência bancária do título.
- TIT_CARTEIRA - passar fixo 'Incluido depois'.
- TIT_LOCPAG - passar fixo 'Qualquer agência bancária'.
- TIT_MOEDA - passar fixo 'R$'.
- TIT_ACEITE - passar fixo 'N'.
- TIT_MODBOL - passar fixo 'PADRAO'

## TB_REMESSA_TITULO
(Registro necessário para quando o título é registrado na instituição bancária.)
- RTI_ID - id da pk auto incremento.
- RTI_TITID - id do titulo bancário ao qual este registro está vinculado.
- RTI_ARMID - id do arquivo remessa ao qual este registro está vinculado.
- RTI_DATAACAO - data que está sendo criado o registro. Caso tenha arquivo remessa, pode usar a data de criação do arquivo remessa.
- RTI_TIPOACAO - ação será fixo. 'INCLUSAO'
- RTI_NOSSONUMERO - nosso número do título ao qual este registro está vinculado.