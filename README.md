# Trabalho jogo Pacman em Assembly
Trabalho na linguagem assembly (link para apresentação:https://youtu.be/I6nawJaza4U?is=p3_5h2Y00fKaRiWZ)RISC (load/store 16 bits) para a matéria **SSC0955 - Introdução a Sistemas Computacionais** 
## Feito pelos alunos: Vitor Dias e Adryann Olivatti 
Criamos o jogo do pacman do zero e fizemos a função sound r0,r1,r2 para o simulador  
Para a informação de como executar o simulador, vá no manualSimulador e utiliza das instruçoes, o material para baixar o simulador está em install_packages, para fazer um jogo cria um arquivo.asm e fala pro montador transformar em arquivo.mif , o criador do simulado é o professor da USP-ICMC Simoes , cujo github é 
https://github.com/simoesusp , segue as fotos abaixo do meu projeto:

## 🎵 Geração de Áudio 

Para gerar a melodia das notas em Assembly sem estourar o buffer e evitar o travamento do processador (já que a instrução de áudio é bloqueante), utilizamos Engenharia de Prompt com Inteligência Artificial para mapear as frequências e as durações das notas.

O esqueleto do prompt utilizado para a automação das melodias foi o seguinte:

```text
Aja como um especialista em teoria musical e programação de baixo nível. 
Sua tarefa é transcrever uma melodia conhecida para a linguagem Assembly de um processador acadêmico customizado de 16 bits (Processador ICMC).

### REGRAS DO HARDWARE:
1. O simulador possui uma instrução de som com a exata sintaxe: `SOUND Rx, Ry, Rz`
2. Os parâmetros são:
   - Rx = Frequência da nota em Hertz (Hz).
   - Ry = Duração da nota em milissegundos (ms).
   - Rz = Tipo de onda (0 = senoide, 1 = quadrada, 2 = triangular, 3 = dente de serra).
3. A instrução SOUND é BLOQUEANTE. Portanto, para o jogo não travar, as durações em (Ry) devem ser extremamente curtas, preferencialmente entre 80ms e 150ms no máximo.

### ESTRUTURA DO CÓDIGO:
- Crie uma sub-rotina com um nome descritivo (ex: TocaMusicaIntro:).
- Faça o push/pop dos registradores usados (r0, r1, r2) no início e fim da sub-rotina.
- Carregue o valor da onda (Rz) apenas uma vez no topo, para economizar instruções.
- Use `loadn r0, #<frequencia>` e `loadn r1, #<duracao>` antes de chamar o `SOUND r0, r1, r2` para cada nota.
```

## Tela inicial:
<img width="651" height="489" alt="Screenshot from 2026-04-22 15-27-16" src="https://github.com/user-attachments/assets/af7eb531-6227-4688-9c14-018bba248bde" />

## game over:

<img width="651" height="489" alt="Screenshot from 2026-04-22 15-27-27" src="https://github.com/user-attachments/assets/7d8fe8f7-804d-482e-94f4-61aa9ab85e70" />

## Fantasmas que podem ser atacados:

<img width="651" height="489" alt="Screenshot from 2026-04-22 15-27-42" src="https://github.com/user-attachments/assets/51a3c6ff-40ed-4336-abfb-a2f7b2203d10" />

## Tela de você venceu:

<img width="651" height="489" alt="Screenshot from 2026-04-22 15-30-17" src="https://github.com/user-attachments/assets/3643d56f-33b2-4559-9f64-610fb693ec99" />
