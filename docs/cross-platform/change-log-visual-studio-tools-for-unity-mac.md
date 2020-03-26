---
title: Log de alterações (Ferramentas do Visual Studio para Unity, Mac) | Microsoft Docs
ms.custom: ''
ms.date: 12/02/2019
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 33a6ac54-d997-4308-b5a0-af7387460849
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 5599153f79b273249e93c48aaa197214d92f5fe7
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80232915"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>Log de alterações (Ferramentas do Visual Studio para Unity, Mac)

Log de alterações de Ferramentas do Visual Studio para Unity.

## <a name="2520"></a>2.5.2.0

Lançado em 23 de março de 2020

### <a name="bug-fixes"></a>Correções de bug

- **Depurador:**

  - Registro fixo de threads no anexo.

## <a name="2510"></a>2.5.1.0

Lançado em 3 de março de 2020

### <a name="new-features"></a>Novos recursos

- **Integração:**

  - Adicionado um supressor para [`IDE0051`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0008.md). Os métodos privados usados com Invoke, InvokeRepeating, StartCoroutine ou StopCoroutine não devem ser marcados como não utilizados.

### <a name="bug-fixes"></a>Correções de bug

- **Integração:**

  - Documentação fixa da OnDrawGizmos/OnDrawGizmosDocumentação selecionada

- **Avaliação:**

  - Inspeção de argumento lambda fixo.

## <a name="2501"></a>2.5.0.1

Lançado em 19 de fevereiro de 2020

### <a name="bug-fixes"></a>Correções de bug

- **Integração:**

  - Verificação de diagnóstico fixa [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/UNT0006.md) para assinatura de mensagem incorreta. Ao inspecionar tipos com vários níveis de herança, este `warning AD0001: Analyzer 'Microsoft.Unity.Analyzers.MessageSignatureAnalyzer' threw an exception of type 'System.ArgumentException' with message 'An item with the same key has already been added`diagnóstico pode falhar com a seguinte mensagem: .

## <a name="2500"></a>2.5.0.0

Lançado em 22 de janeiro de 2020

### <a name="new-features"></a>Novos recursos

- **Integração:**

  - Adicionado suporte para arquivos HLSL.
  
  - Mudou para uma nova ui de diálogo de pasta.
  
  - Comutado para uma nova grade de propriedade acessível para configurações.

  - Adicionado um supressor para [`IDE0051`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0006.md). Campos privados `SerializeField` com o atributo não devem ser marcados como não utilizados.

  - Adicionado um supressor para [`CS0649`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0007.md). Campos com `SerializeField` o atributo não devem ser marcados como não atribuídos.  

### <a name="bug-fixes"></a>Correções de bug

- **Integração:**

  - Geração fixa`GenerateTargetFrameworkMonikerAttribute` de projetos (o alvo nem sempre foi localizado corretamente)

- **Avaliação:**

  - Avaliação de string fixa (não usando chamadas ToString()

## <a name="2420"></a>2.4.2.0

Lançado em 3 de dezembro de 2019

### <a name="bug-fixes"></a>Correções de bug

- **Integração:**

  - Corrigimos diagnósticos com interfaces definidas pelo usuário.

  - Corrigido dicas de ferramentas rápidas com expressões malformadas.
  
## <a name="2410"></a>2.4.1.0

Lançado em 6 de novembro de 2019

### <a name="new-features"></a>Novos recursos

- **Integração:**

  - Adicionado suporte aos processos de fundo do Unity. (O depurador é capaz de se conectar automaticamente ao processo principal em vez de um processo filho).

  - Adicionada uma dica de ferramenta rápida para mensagens Unity, exibindo a documentação associada.

### <a name="bug-fixes"></a>Correções de bug

- **Integração:**

  - Corrigimos o analisador de comparação de etiquetas `UNT0002` com expressões binárias avançadas e invocações.

### <a name="deprecated-features"></a>Recursos preteridos

- **Integração:**

  - Daqui para frente, o Visual Studio Tools for Unity só suportará o Visual Studio 2017+.

## <a name="2400"></a>2.4.0.0

Lançado em 15 de outubro de 2019

### <a name="new-features"></a>Novos recursos

- **Integração:**

  - Adicionado um supressor para `IDE0060` (parâmetro não utilizado) para todas as mensagens de Unidade.

  - Adicionada uma dica de ferramenta `TooltipAttribute`rápida para campos marcados com . (Isso funcionará para um simples acessório de obter usando este campo também).

## <a name="2330"></a>2.3.3.0

Lançado em 23 de setembro de 2019

### <a name="new-features"></a>Novos recursos

- **Integração:**

  - Adicionou um novo supressor para IDE0060, para evitar que o IDE apareça uma correção rápida para remover parâmetros não utilizados.
    - `USP0005`para `IDE0060`: As mensagens de unidade são invocadas pelo tempo de execução da Unidade.

## <a name="2320"></a>2.3.2.0

Lançado em 16 de setembro de 2019

### <a name="new-features"></a>Novos recursos

- **Integração:**

  - Aprofundamos o entendimento que o Visual Studio tem para projetos unity adicionando novos diagnósticos específicos ao Unity. Também tornamos o IDE mais inteligente, suprimindo diagnósticos C# gerais que não se aplicam a projetos do Unity. Por exemplo, o IDE não mostrará uma correção `readonly` rápida para alterar uma variável de inspetor para a qual impediria que você modificasse a variável no Unity Editor.
    - `UNT0001`: As mensagens de unidade são chamadas pelo tempo de execução, mesmo que estejam vazias, não as declare para evitar o processamento de desesseray pelo tempo de execução da Unidade.
    - `UNT0002`: A comparação de caracteres usando a igualdade de strings é mais lenta do que o método compareTag incorporado.
    - `UNT0003`: O uso da forma genérica de GetComponent é preferido para a segurança do tipo.
    - `UNT0004`: A mensagem de atualização é dependente da taxa de quadros e deve usar time.deltaTime em vez de Time.fixedDeltaTime.
    - `UNT0005`: A mensagem FixedUpdate é independente da taxa de quadros e deve usar time.fixedDeltaTime em vez de Time.deltaTime.
    - `UNT0006`: Foi detectada uma assinatura de método incorreta para esta mensagem unity.
    - `UNT0007`: A unidade substitui o operador de comparação nula para objetos unity que é incompatível com a coalescção nula.
    - `UNT0008`: A unidade substitui o operador de comparação nula para objetos Unity que é incompatível com a propagação nula.
    - `UNT0009`: Ao aplicar o atributo InitializeOnLoad a uma classe, você precisa fornecer um construtor estático. O atributo InitializeOnLoad verifica se ele será chamado quando o editor for iniciado.
    - `UNT0010`: MonoComportamentos só devem ser criados usando AddComponent(). O MonoBehaviour é um componente e precisa ser anexado a um GameObject.
    - `UNT0011`: ScriptableObject só deve ser criado usando CreateInstance(). ScriptableObject precisa ser criado pelo mecanismo do Unity para manipular métodos de mensagem do Unity.
    - `USP0001`para: `IDE0029`Os objetos de unidade não devem usar coalescção nula.
    - `USP0002`para: `IDE0031`Os objetos de unidade não devem usar propagação nula.
    - `USP0003`para `IDE0051`: As mensagens de unidade são invocadas pelo tempo de execução da Unidade.
    - `USP0004`para `IDE0044`: Campos com um atributo SerializeField não devem ser feitos somente de leitura.

## <a name="2310"></a>2.3.1.0

Lançado em 4 de setembro de 2019

### <a name="new-features"></a>Novos recursos

- **Avaliação:**

  - Adicionado suporte para melhor exibição `List<object>` de `List'1[[System.Object, <corlib...>]]`tipo, ou seja, em vez de .

  - Suporte adicionado para acesso a membros `p->data->member`do ponteiro, ou seja. .

  - Adicionado suporte para conversões implícitas em iniciadores `new byte [] {1,2,3,4}`de matriz, ou seja, .

  - Adicionado suporte para o editor hexa ao inspecionar matrizes de bytes e strings.

## <a name="2300"></a>2.3.0.0

Lançado em 13 de agosto de 2019

### <a name="bug-fixes"></a>Correções de bug

- **Avaliação:**

  - Corrigimos problemas de etapas com exceções.

  - Avaliação fixa de pseudo identificadores (como $exception).

  - Evite falhas ao desfazer endereços inválidos.  

  - Corrigido problema com domínios deaplicativos descarregados.

## <a name="2200"></a>2.2.0.0

Lançado em 25 de julho de 2019

### <a name="bug-fixes"></a>Correções de bug

- **Avaliação:**

  - corrigida a inspeção com tipos IntPtr.

- **Depurador:**

  - corrigida a manipulação de catchpoints e pontos de interrupção de função.

## <a name="2130"></a>2.1.3.0

Lançado em 9 de julho de 2019

### <a name="new-features"></a>Novos recursos

- **Depurador:**

  - adicionado suporte para captura de subclasses de exceções;

  - adicionado suporte a protocolo MDS 2.51.

- **Integração:**

  - adicionado suporte para arquivos asmdef.

  - Mude para o modo de renomeação quando um arquivo for adicionado de um modelo (para imitar o comportamento do Editor do Unity).

### <a name="bug-fixes"></a>Correções de bug

- **Integração:**

  - corrigida a manipulação de mensagens malformadas durante a comunicação com players do Unity.

- **Avaliação:**

  - corrigida a manipulação de namespaces em expressões.

## <a name="2120"></a>2.1.2.0

Lançado em 2 de julho de 2019

### <a name="bug-fixes"></a>Correções de bug

- **Avaliação:**

  - corrigido o relatório de erros com expressões não analisáveis.

## <a name="2110"></a>2.1.1.0

Lançado em 27 de junho de 2019

### <a name="new-features"></a>Novos recursos

- **Integração:**

  - Atualização da API MonoBehaviour para 2019.1.

### <a name="bug-fixes"></a>Correções de bug

- **Integração:**

  - corrigido o desempenho do Gerenciador de Projetos do Unity.

  - Correção de emissão de relatórios de erros e avisos para a saída quando a compilação leve está habilitada.

  - Desempenho de construção leve e fixo.

## <a name="2100"></a>2.1.0.0

Lançado em 20 de junho de 2019

### <a name="new-features"></a>Novos recursos

- **Integração:**

  - Desabilitada a compilação completa para projetos Unity, em favor de usar os erros e avisos do IntelliSense. Na verdade, o Unity cria uma solução do Visual Studio com projetos de biblioteca de classes que representam o que o Unity está fazendo internamente. Dito isso, o resultado da compilação no Visual Studio nunca é usado ou selecionado pelo Unity quando seu pipeline de compilação é fechado. A criação no Visual Studio está apenas consumindo recursos para nada. Se você precisar de um build completo por ter ferramentas ou uma configuração que dependa disso, poderá desabilitar essa otimização (Configurações/Ferramentas para Unity/Desabilitar o build completo de projetos).
  
  - Adicionado suporte para pacotes Unity no UPE. Somente pacotes referenciados (usando manifest.json na pasta `Packages`) e pacotes locais (incorporados na pasta `Packages`) são visíveis.

## <a name="2021"></a>2.0.2.1

Lançamento em 30 de maio de 2019

### <a name="new-features"></a>Novos recursos

- **Integração:**

  - Ícone personalizado adicionado para destinos de execução do Unity.

## <a name="2020"></a>2.0.2.0

Lançado em 2 de abril de 2019

### <a name="new-features"></a>Novos recursos

- **Integração:**

  - Adicionado suporte para atualizar automaticamente o banco de dados de ativos do Unity ao salvar. Isso é habilitado por padrão e acionará uma recompilação no lado Unity ao salvar um script no Visual Studio. Você pode desativar esse recurso em Ferramentas\Opções\Ferramentas para Unity\Atualizar AssetDatabase do Unity ao salvar.

  - Adicionado suporte para a configuração de instalação preferencial do Unity para obter a documentação offline.

  - Adicionado menu de contexto para o novo editor.

### <a name="bug-fixes"></a>Correções de bug

- **Depurador:**

  - Correção de filtragem de montagem e inspeção de estrutura com quadros vazios.

## <a name="2011"></a>2.0.1.1
 
 Lançado em 26 de março de 2019

### <a name="bug-fixes"></a>Correções de bug

- **Integração:**

  - Tornar temporariamente o Mono o depurador utilizável padrão e único para este lançamento muito específico.

## <a name="2006"></a>2.0.0.6

Lançado em 26 de março de 2019

### <a name="new-features"></a>Novos recursos

- **Integração:**

  - Adicionado suporte para "Anexar ao Unity e Reproduzir".

## <a name="2005"></a>2.0.0.5

Lançado em 20 de março de 2019

### <a name="new-features"></a>Novos recursos

- **Geração de projetos:**

  - Preservar propriedades externas ao processar o arquivo da solução.
  
- **Avaliação:**

  - Adicionado suporte para nomes qualificados por alias (somente o namespace global por enquanto). Portanto, o avaliador de expressão agora aceita tipos usando o formato global::namespace.type.

  - Adicionado suporte para o formulário `pointer[index]`, que é semanticamente idêntico ao formulário de desreferenciamento de ponteiro `*(pointer+index)`.

## <a name="2004"></a>2.0.0.4

Lançado em 5 de março de 2019

### <a name="new-features"></a>Novos recursos

- **Integração:**

  - Atualizei a `ScriptableObject` API.

### <a name="bug-fixes"></a>Correções de bug

- **Integração:**

  - Removidos namespaces de modelos.

## <a name="2003"></a>2.0.0.3
 
 Lançado em 5 de março de 2019

### <a name="new-features"></a>Novos recursos

- **Geração de projetos:**

  - Campos públicos e serializados não irão mais gerar avisos. Suprimimos automaticamente os `CS0649` avisos `IDE0051` e compiladores em projetos da Unity que criaram essas mensagens.

- **Integração:**

  - Avisar para anexar a uma instância específica se mais de um processo do Unity estiver em execução.

- **Avaliação:**

  - Adicionado suporte para funções locais.

### <a name="bug-fixes"></a>Correções de bug

- **Depurador:**

  - Correção de atributo personalizado de leitura em argumentos nomeados ao usar versões de protocolo antigas.

## <a name="2002"></a>2.0.0.2

Lançado em 4 de fevereiro de 2019

### <a name="new-features"></a>Novos recursos

- **Integração:**

  - Atualização da API MonoBehaviour.

### <a name="bug-fixes"></a>Correções de bug

- **Depurador:**

  - Correção de valores primitivos de configuração no depurador.

## <a name="2001"></a>2.0.0.1

Lançado em 4 de dezembro de 2018

### <a name="bug-fixes"></a>Correções de bug

- **Integração:**

  - Correção de pacote de instalação autossuficiente.

## <a name="2000"></a>2.0.0.0
 Lançado em 4 de dezembro de 2018

### <a name="new-features"></a>Novos recursos

- **Depurador:**

  - Substituição do depurador do Unity no Mac pelo mesmo principal depurador Unity do Windows.

  - Substituição do NRefactory em favor do Roslyn para avaliação de expressão.

  - Adicionado suporte para ponteiros: desreferenciamento, conversão e aritmética de ponteiro (tanto o Unity 2018.2+ quanto o novo runtime são necessários para isso).

  - Adicionado suporte para o modo de exibição de ponteiro de matriz (como no C++). Selecione uma expressão de ponteiro e acrescente uma vírgula e o número de elementos que você deseja ver.

  - Adicionado suporte para construções assíncronas.

  - Adicionado suporte para as pseudovariáveis (identificadores de objeto e de exceção).

### <a name="bug-fixes"></a>Correções de bug

- **Depurador:**

  - Correção de avaliação de expressão com expressões malformadas ou sem suporte.

## <a name="1700"></a>1.7.0.0

Lançado em 13 de novembro de 2018

### <a name="new-features"></a>Novos recursos

- **Depurador:**

  - Adição de outras informações de cliente (IP, nome do computador) à caixa de diálogo Anexar.

### <a name="bug-fixes"></a>Correções de bug

- **Depurador:**

  - Corrigido um deadlock na biblioteca usada para se comunicar com o mecanismo de depuração do Unity, causando o congelamento do Visual Studio ou Unity, especialmente ao pressionar "Anexar ao Unity" ou ao reiniciar o jogo.

- **Integração:**

  - Correção da ativação de plug-in do Unity quando outro editor padrão é selecionado.

  - Correção da criação do modelo de arquivo do Unity.

## <a name="1602"></a>1.6.0.2

Lançado em 24 de julho de 2018

### <a name="bug-fixes"></a>Correções de bug

- **Integração:**

  - Foi revertida a solução alternativa para um bug de desempenho do Unity que foi corrigido pelo Unity.

## <a name="1601"></a>1.6.0.1

Lançado em 10 de julho de 2018

### <a name="bug-fixes"></a>Correções de bug

- **Integração:**

  - Suporte à coloração de código de Sombreador corrigido.

## <a name="1600"></a>1.6.0.0

Lançado em 26 de junho de 2018

### <a name="bug-fixes"></a>Correções de bug

- **Assistentes:**

  - Erro de digitação corrigido com a mensagem OnApplicationFocus.

- **Geração de projetos:**

  - Solução alternativa temporária para um bug de desempenho do Unity: armazenar em cache MonoIslands ao gerar projetos.

  - Não converta mais um pdb portátil para mdb ao usar o novo runtime do Unity.

## <a name="1502"></a>1.5.0.2

Lançado em 18 de abril de 2018

### <a name="new-features"></a>Novos recursos

- **Integração:**

  - Adicionado suporte para a conclusão de código básico do Sombreador.

  - Adicionado suporte para ativar/desativar comentários em arquivos do Sombreador.

## <a name="1501"></a>1.5.0.1

Lançado em 28 de março de 2018

### <a name="new-features"></a>Novos recursos

- **Integração:**

  - Adicionado suporte para modelos adicionais no Explorador de Projeto do Unity.

## <a name="1500"></a>1.5.0.0

Lançado em 21 de março de 2018

### <a name="new-features"></a>Novos recursos

- **Integração:**

  - Adicionado suporte para detectar e anexar a players Android conectados por USB.

## <a name="1403"></a>1.4.0.3

Lançado em 5 de março de 2018

### <a name="new-features"></a>Novos recursos

- **Geração de projetos:**

  - Adicionado o suporte para o gerador de projeto novo no Unity 2018.1.

- **Integração:**

  - Adicionado painel de opções para configurações dedicadas.

## <a name="1402"></a>1.4.0.2

Lançado em 24 de janeiro de 2018

### <a name="bug-fixes"></a>Correções de bug

- **Geração de projetos:**

  - Correção da detecção de versão Mono.

- **Integração:**

  - Correção dos problemas de timing com 2018.1 e ativação de plug-in.

  - Corrigidas as notificações ao detectar um novo player.

## <a name="1401"></a>1.4.0.1

Lançado em 23 de janeiro de 2018

### <a name="bug-fixes"></a>Correções de bug

- **Integração:**

  - Corrigida a funcionalidade de Expandir/Recolher pastas ao clicar duas vezes

## <a name="1400"></a>1.4.0.0

Lançado em 13 de dezembro de 2017

### <a name="new-features"></a>Novos recursos

- **Geração de projetos:**

  - Suporte adicionado para o .NET Standard.

### <a name="bug-fixes"></a>Correções de bug

- **Integração:**

  - Correção de pdb automático para conversão de símbolo de depuração de mdb.

## <a name="1301"></a>1.3.0.1

Lançado em 12 de dezembro de 2017

### <a name="bug-fixes"></a>Correções de bug

- **Integração:**

  - Correção de chamada indireta para EditorPrefs.GetBool afetando o inspetor ao tentar alterar o tamanho da matriz.

- **Assistentes:**

  - Atualize o contexto do roslyn antes de inserir o método.

## <a name="1300"></a>1.3.0.0

Lançado em 20 de novembro de 2017

### <a name="new-features"></a>Novos recursos

- **Assistentes:**

  - Adicionado o assistente "Implementar mensagem do Unity".

  - Adicionado suporte para nova API de conclusão no VS para Mac 7.4.

## <a name="1200"></a>1.2.0.0

Lançado em 23 de outubro de 2017

### <a name="new-features"></a>Novos recursos

- **Depurador:**

  - Suporte adicionado para arquivos de símbolo de depuração portátil.

### <a name="bug-fixes"></a>Correções de bug

- **Geração de projetos:**

  - Correção da extensão .dll extra adicionada por engano ao arquivo do assembly.

  - Não force o sinalizador AllowAttachedDebuggingOfEditor do Unity, uma vez que o padrão agora é ‘true’.

## <a name="1103"></a>1.1.0.3

Lançado em 23 de outubro de 2017

### <a name="new-features"></a>Novos recursos

- **Geração de projetos:**

  - Suporte adicionado para o perfil do .NET 4.6.

## <a name="1102"></a>1.1.0.2

Lançado em 8 de agosto de 2017

### <a name="new-features"></a>Novos recursos

- **Depurador:**

  - Iniciar a caixa de diálogo Anexar ao processo se não souber a qual Unity anexar.

- **Geração de projetos:**

  - Sempre habilite a opção de compilação não segura quando o Unity 5.6 for usado.

## <a name="1101"></a>1.1.0.1

Lançado em 20 de julho de 2017

### <a name="new-features"></a>Novos recursos

- **Integração:**

  - Adicionado suporte para recursos localizados.

## <a name="1100"></a>1.1.0.0

Lançado em 12 de julho de 2017

### <a name="new-features"></a>Novos recursos

- **Integração:**

  - Adicionado suporte para anexar a players e editores por meio da janela Anexar ao processo.

- **Geração de projetos:**

  - Corrigidas referências de nome de assembly com arquivos mcs.rsp.

  - Adicionado suporte para unidades de compilação assembly.json.

  - Corrigidas definições com níveis de API.

### <a name="bug-fixes"></a>Correções de bug

- **Integração:**

  - Corrigida mensagem de erro do sombreador ao compilar.

## <a name="1001"></a>1.0.0.1

Lançado em 4 de maio de 2017

### <a name="bug-fixes"></a>Correções de bug

- **Integração:**

  - Corrigido acompanhamento de documento ativo com projetos regulares e híbridos.

## <a name="1000"></a>1.0.0.0

Lançado em 3 de maio de 2017
