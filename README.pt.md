# youtube-vers-agent

Uma habilidade do Claude Code que transforma tutoriais do YouTube em habilidades do Claude Code através de verificação dual-fonte (Claude local + Gemini) e cruzamento de especificações.

## Descrição

Esta habilidade converte o conteúdo de tutoriais do YouTube em habilidades do Claude Code estruturadas através de:
1. Extrair conceitos-chave e procedimentos das transcrições de vídeo
2. Verificar informações através de validação dual-fonte (vídeo + documentação)
3. Criar arquivos SKILL.md corretamente formatados seguindo as convenções do Claude Code
4. Garantir precisão e completude através de referências cruzadas

## Quando usar

Use esta habilidade quando você quiser:
- Converter conteúdo educativo do YouTube em habilidades do Claude Code reutilizáveis
- Criar habilidades baseadas em vídeos tutoriais sobre ferramentas de desenvolvimento, frameworks ou metodologias
- Garantir a precisão das habilidades através de verificação em relação à documentação oficial
- Construir uma biblioteca de habilidades verificadas a partir de recursos de aprendizagem em vídeo

## Fluxo da habilidade

### 1. Fase de análise de vídeo
- Processe o vídeo do YouTube usando a habilidade watch para extrair a transcrição e os quadros-chave
- Identifique os tópicos principais, procedimentos e exemplos de código apresentados
- Estruture os objetivos e resultados de aprendizagem

### 2. Verificação dual-fonte
- Para cada conceito/procedimento-chave, consulte a documentação oficial usando as habilidades context7-mcp ou find-docs
- Cruzere o conteúdo de vídeo com fontes autoritativas
- Anote quaisquer discrepâncias ou diferenças de versão
- Verifique se os exemplos de código funcionam como demonstrado

### 3. Criação da habilidade
- Gere um arquivo SKILL.md corretamente formatado seguindo as convenções do Claude Code
- Inclua uma descrição clara, diretrizes de uso e um fluxo de trabalho passo a passo
- Referencie tanto a fonte de vídeo quanto as fontes de documentação usadas para a verificação
- Adicione recomendações de ferramentas apropriadas baseadas nos procedimentos verificados

### 4. Garantia de qualidade
- Teste os exemplos de código ou procedimentos mencionados
- Valide que a habilidade siga os padrões de formatação de habilidades do Claude Code
- Assegure que a habilidade forneça orientação acionável e verificável

## Saída

Produz um arquivo SKILL.md completo no diretório apropriado .claude/skills/ que:
- Define claramente o propósito e a aplicabilidade da habilidade
- Fornece diretrizes de uso específicas
- Descreve um fluxo de trabalho verificável
- Referencia as fontes usadas para a verificação dual-fonte
- Segue as convenções de habilidades do Claude Code

## Ferramentas necessárias

- watch: Para processar o conteúdo de vídeos do YouTube
- context7-mcp ou find-docs: Para verificação dual-fonte em relação à documentação oficial
- Bash: Para operações de arquivos e criação de habilidades

## Instalação

1. Clone este repositório:
   ```bash
   git clone https://github.com/Zero-Piege/youtube-vers-agent
   ```

2. Copie a habilidade para o seu diretório de habilidades do Claude Code:
   ```bash
   cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
   ```

3. Recarregue os plugins:
   ```bash
   /reload-plugins
   ```

## Uso

Após a instalação, você pode usar a habilidade fornecendo uma URL do YouTube e especificando o que deseja construir:

```
/youtube-vers-agent [URL do YouTube] [o que extrair] [o que construir]
```

Exemplo:
```
/youtube-vers-agent https://youtu.be/zke3bTtvmLo Todo o projeto Uma habilidade do Claude Code
```

## Exemplo de uso

Transforme um tutorial do YouTube sobre a criação de componentes React em uma habilidade do Claude Code:
1. Use a habilidade watch para extrair a transcrição do vídeo e os pontos-chave
2. Use context7-mcp para verificar os padrões de criação de componentes React em relação à documentação oficial do React
3. Crie SKILL.md com procedimentos verificados para criar componentes React no Claude Code
4. Inclua referências tanto ao tutorial do YouTube quanto à documentação do React utilizada

## Padrões de verificação

Todas as habilidades criadas devem:
- Referenciar pelo menos duas fontes independentes (vídeo + documentação)
- Incluir etapas específicas e acionáveis
- Fornecer diretrizes de uso claras
- Seguir o formato estabelecido das habilidades do Claude Code
- Conter procedimentos verificáveis que possam ser testados

## Licença

Licença MIT - consulte o arquivo [LICENSE](LICENSE) para detalhes.