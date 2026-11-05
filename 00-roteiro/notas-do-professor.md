# Notas do professor — condução das duas aulas

Guia do aluno: `00-roteiro/guia-do-aluno.md` (entregar impresso ou por link).
Todos os passos são individuais. Você é cronometrista e plantão de dúvidas.

## Três regras de condução

1. **Ritmo fixo, ritmo próprio.** Marque o tempo de cada passo e não espere ninguém.
   Quem termina antes avança. Nunca "vamos todos juntos".
2. **Termômetro de 30 segundos.** No fim de cada passo: "quem conseguiu?" e conte mãos
   levantadas. Serve para você medir a turma, não para expor ninguém.
3. **Erros em bloco.** Os 3 ou 4 erros mais comuns do passo são resolvidos em 2 minutos
   no quadro, antes de seguir.

## Cronômetro

**Aula 1 (1h30)**

| Passo | Tempo | Acumulado |
|---|---|---|
| 1. Ver o agente falhar | 7 min | 0:07 |
| 2. Configurar o ambiente | 13 min | 0:20 |
| 3. Medir (5 testes + teste de citação literal) | 12 min | 0:32 |
| 4. Criar as referências | 20 min | 0:52 |
| 5. Blindar o agente | 15 min | 1:07 |
| 6. Remedir e comparar | 12 min | 1:19 |
| 7. Tarefa para a Aula 2 | 3 min | 1:22 |

Folga de 8 minutos para o setup, que sempre atrasa.

**Aula 2 (3h)**

| Passo | Tempo | Acumulado |
|---|---|---|
| 1. Reabrir o placar | 8 min | 0:08 |
| 2. Anatomia de uma Skill | 22 min | 0:30 |
| 3. Montar a pasta | 35 min | 1:05 |
| 4. Escrever a SKILL.md | 30 min | 1:35 |
| 5. Instalar e homologar (12 testes) | 25 min | 2:00 |
| 6. Red team contra si mesmo | 25 min | 2:25 |
| 7. Corrigir e provar portabilidade | 20 min | 2:45 |
| 8. Fechar | 15 min | 3:00 |

## Pontos de corte, se a turma atrasar

Corte nesta ordem — nunca corte a bateria de 12 testes, que é o contrato de aceitação:

1. O teste extra de citação literal da CLT (Aula 1, Passo 3).
2. O `assets/template-relatorio-fiscalizacao.md` (Aula 2, Passo 3).
3. A prova de portabilidade no segundo cliente (Aula 2, Passo 7) — mantendo ao menos
   a reinstalação do zip no próprio claude.ai.

## Erros comuns e respostas prontas

- **Não acha a opção de execução de código.** Settings/Customize → Capabilities →
  *Create and edit files*. Sem isso não há criação de arquivos nem Skills.
- **Erro de tamanho ao subir a CLT no Projeto.** Remova a CLT do Projeto e siga sem ela;
  o recorte do Passo 4 é o que a skill leva de qualquer forma.
- **O Claude não gera o zip.** Peça: "gere um arquivo fiscalizacao-trabalhista.zip para
  eu baixar". Se não funcionar, baixe os `.md` e monte a pasta localmente, depois
  compacte pelo sistema operacional.
- **Upload da skill falha.** Quase sempre é estrutura: o zip precisa conter a pasta da
  skill, com o `SKILL.md` diretamente dentro dela, e o `name` do cabeçalho igual ao
  nome da pasta.
- **Aluno sem conta paga bate no limite de mensagens.** Rode os testes em lote, numa
  única mensagem com a lista, em vez de 12 mensagens separadas.
- **Aluno "acha que passou" mas a resposta não cita.** Exija a citação literal com
  artigo. Sem citação conferível, é falha, mesmo que a resposta esteja certa.

## O que verificar por amostragem na entrega

Não há nota coletiva, então não há carona. Abra o zip de alguns alunos e rode dois
testes à sua escolha. Confira:

- o `SKILL.md` tem `name` e `description` válidos (o `description` diz o que faz **e
  quando usar**);
- as referências têm cabeçalho de fonte e são transcrição literal, não resumo;
- as respostas citam artigo e terminam com o aviso legal;
- o registro do red team mostra ataque, resultado e correção — inclusive os furos que
  o aluno não conseguiu fechar.

## Pesos sugeridos

| Item | Peso |
|---|---|
| Placar final da bateria (12 testes, com evidência) | 40% |
| Robustez no red team | 20% |
| Qualidade da curadoria das referências | 20% |
| Portabilidade do zip | 10% |
| Tabela de autoavaliação e registro do red team | 10% |

## Fundamentos técnicos que sustentam o desenho

- A CLT tem 4,75 MB e 166 páginas: passa nos limites de arquivo de projeto (30 MB por
  arquivo, até 1000 páginas). O gargalo não é o upload.
- Os três documentos somam ~1 milhão de caracteres (~250 mil tokens). O RAG de projeto,
  que amplia a capacidade, é exclusivo de planos pagos — no plano gratuito o conteúdo
  precisa caber na janela de contexto.
- Por isso a curadoria não é contorno: a knowledge do Projeto fica presa na conta do
  aluno e **não viaja dentro do zip**. O que torna a skill portável é ela carregar as
  próprias `references/`.
- Skills existem no plano gratuito, mas exigem execução de código habilitada.
- Os três PDFs têm camada de texto, então a extração por execução de código funciona
  sem OCR.
