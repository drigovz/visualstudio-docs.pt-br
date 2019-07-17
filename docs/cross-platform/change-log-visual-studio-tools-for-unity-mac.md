---
title: Log de alterações (Ferramentas do Visual Studio para Unity, Mac) | Microsoft Docs
ms.custom: ''
ms.date: 04/02/2019
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 33a6ac54-d997-4308-b5a0-af7387460849
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: e5bc02948d410d465d7ac1be798ff17ebc5daaf9
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67821510"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>Log de alterações (Ferramentas do Visual Studio para Unity, Mac)

Log de alterações de Ferramentas do Visual Studio para Unity.

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

## <a name="2004"></a>2.0.0.4

Lançado em 5 de março de 2019

### <a name="new-features"></a>Novos recursos

- **Integração:**

  - Atualização da API ScriptableObject.

### <a name="bug-fixes"></a>Correções de bug

- **Integração:**

  - Removidos namespaces de modelos.

## <a name="2003"></a>2.0.0.3
 Lançado em 5 de março de 2019

### <a name="new-features"></a>Novos recursos

- **Geração do Projeto:**

  - Campos públicos e serializados não irão mais gerar avisos. Suprimimos automaticamente os avisos do compilador CS0649 e IDE0051 em projetos Unity que criaram essas mensagens.

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
