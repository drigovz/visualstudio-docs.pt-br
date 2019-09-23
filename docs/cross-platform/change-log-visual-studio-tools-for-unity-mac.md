---
title: Log de alterações (Ferramentas do Visual Studio para Unity, Mac) | Microsoft Docs
ms.custom: ''
ms.date: 09/18/2019
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 33a6ac54-d997-4308-b5a0-af7387460849
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 897851055bd2eacc10edea9fdff2ab3ecd61b963
ms.sourcegitcommit: 88f576ac32af31613c1a10c1548275e1ce029f4f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71185967"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>Log de alterações (Ferramentas do Visual Studio para Unity, Mac)

Log de alterações de Ferramentas do Visual Studio para Unity.

## <a name="2330"></a>2.3.3.0

Lançado em 23 de setembro de 2019

### <a name="new-features"></a>Novos recursos

- **Integração:**

  - Foi adicionado um novo supressor para IDE0060, para impedir que o IDE mostre uma correção rápida para remover parâmetros não utilizados.
    - `USP0005`para `IDE0060`: As mensagens do Unity são invocadas pelo tempo de execução do Unity.

## <a name="2320"></a>2.3.2.0

Lançado em 16 de setembro de 2019

### <a name="new-features"></a>Novos recursos

- **Integração:**

  - Nós aprofundamos a compreensão de que o Visual Studio tem para projetos do Unity adicionando novos diagnósticos específicos ao Unity. Também tornamos o IDE mais inteligente, suprimindo diagnósticos C# gerais que não se aplicam a projetos do Unity. Por exemplo, o IDE não mostrará uma correção rápida para alterar uma variável de Inspetor `readonly` para a qual impediria que você modificasse a variável no editor do Unity.
    - `UNT0001`: as mensagens do Unity serão chamadas pelo tempo de execução mesmo se estiverem vazias. Não as declare para evitar o processamento de desnecessário pelo tempo de execução do Unity.
    - `UNT0002`: a comparação de marcas usando a igualdade de cadeia de caracteres é mais lenta do que o método CompareTag interno.
    - `UNT0003`: o uso da forma genérica de GetComponent é preferencial para a segurança de tipos.
    - `UNT0004`: a mensagem de atualização é dependente de taxa de quadros e deve usar Time.deltaTime em vez de Time.fixedDeltaTime.
    - `UNT0005`: a mensagem FixedUpdate é independente de taxa de quadros e deve usar Time.fixedDeltaTime em vez de Time.deltaTime.
    - `UNT0006`: Uma assinatura de método incorreta foi detectada para esta mensagem do Unity.
    - `UNT0007`: o Unity substitui o operador de comparação nula para objetos do Unity que é incompatível com a união nula.
    - `UNT0008`: o Unity substitui o operador de comparação nula para objetos do Unity que é incompatível com a propagação nula.
    - `UNT0009`: ao aplicar o atributo InitializeOnLoad a uma classe, você precisa fornecer um construtor estático. O atributo InitializeOnLoad verifica se ele será chamado quando o editor for iniciado.
    - `UNT0010`: MonoBehaviours só deve ser criado usando AddComponent(). O MonoBehaviour é um componente e precisa ser anexado a um GameObject.
    - `UNT0011`: ScriptableObject só deve ser criado usando CreateInstance(). ScriptableObject precisa ser criado pelo mecanismo do Unity para manipular métodos de mensagem do Unity.
    - `USP0001`para `IDE0029`: Os objetos do Unity não devem usar a União nula.
    - `USP0002`para `IDE0031`: Os objetos do Unity não devem usar a propagação nula.
    - `USP0003`para `IDE0051`: As mensagens do Unity são invocadas pelo tempo de execução do Unity.
    - `USP0004`para `IDE0044`: Os campos com um atributo Serializefield não devem ser criados somente leitura.

## <a name="2310"></a>2.3.1.0

lançado em 4 de setembro de 2019

### <a name="new-features"></a>Novos recursos

- **Avaliação:**

  - Adição de suporte para melhor exibição de tipo, `List<object>` ou seja `List'1[[System.Object, <corlib...>]]`, em vez de.

  - Suporte adicionado para acesso de membro de ponteiro, `p->data->member`ou seja,.

  - Suporte adicionado para conversões implícitas em inicializadores de matriz, ou `new byte [] {1,2,3,4}`seja,.

  - Suporte adicionado para o editor hexadecimal ao inspecionar matrizes de bytes e cadeias de caracteres.

## <a name="2300"></a>2.3.0.0

lançado em 13 de agosto de 2019

### <a name="bug-fixes"></a>Correções de bug

- **Avaliação:**

  - Correção de problemas de depuração com exceções.

  - Correção da avaliação de pseudo identificadores (como $exception).

  - Impedir falha ao desreferenciar endereços inválidos.  

  - Corrigido o problema com AppDomains descarregados.

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

- **Geração do Projeto:**

  - Preservar propriedades externas ao processar o arquivo da solução.
  
- **Avaliação:**

  - Adicionado suporte para nomes qualificados por alias (somente o namespace global por enquanto). Portanto, o avaliador de expressão agora aceita tipos usando o formato global::namespace.type.

  - Adicionado suporte para o formulário `pointer[index]`, que é semanticamente idêntico ao formulário de desreferenciamento de ponteiro `*(pointer+index)`.

## <a name="2004"></a>2.0.0.4

Lançado em 5 de março de 2019

### <a name="new-features"></a>Novos recursos

- **Integração:**

  - A `ScriptableObject` API foi atualizada.

### <a name="bug-fixes"></a>Correções de bug

- **Integração:**

  - Removidos namespaces de modelos.

## <a name="2003"></a>2.0.0.3
 
 Lançado em 5 de março de 2019

### <a name="new-features"></a>Novos recursos

- **Geração do Projeto:**

  - Campos públicos e serializados não irão mais gerar avisos. Suprimemos automaticamente os avisos de `CS0649` compilador `IDE0051` e em projetos do Unity que criaram essas mensagens.

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

  - Adicionado suporte para ponteiros: desreferenciamento, conversão e aritmética de ponteiro (tanto o Unity 2018.2+ quanto o novo tempo de execução são necessários para isso).

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

- **Geração do Projeto:**

  - Solução alternativa temporária para um bug de desempenho do Unity: armazenar em cache MonoIslands ao gerar projetos.

  - Não converta mais um pdb portátil para mdb ao usar o novo tempo de execução do Unity.

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

- **Geração do Projeto:**

  - Adicionado o suporte para o gerador de projeto novo no Unity 2018.1.

- **Integração:**

  - Adicionado painel de opções para configurações dedicadas.

## <a name="1402"></a>1.4.0.2

Lançado em 24 de janeiro de 2018

### <a name="bug-fixes"></a>Correções de bug

- **Geração do Projeto:**

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

- **Geração do Projeto:**

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

- **Geração do Projeto:**

  - Correção da extensão .dll extra adicionada por engano ao arquivo do assembly.

  - Não force o sinalizador AllowAttachedDebuggingOfEditor do Unity, uma vez que o padrão agora é ‘true’.

## <a name="1103"></a>1.1.0.3

Lançado em 23 de outubro de 2017

### <a name="new-features"></a>Novos recursos

- **Geração do Projeto:**

  - Suporte adicionado para o perfil do .NET 4.6.

## <a name="1102"></a>1.1.0.2

Lançado em 8 de agosto de 2017

### <a name="new-features"></a>Novos recursos

- **Depurador:**

  - Iniciar a caixa de diálogo Anexar ao processo se não souber a qual Unity anexar.

- **Geração do Projeto:**

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

- **Geração do Projeto:**

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
