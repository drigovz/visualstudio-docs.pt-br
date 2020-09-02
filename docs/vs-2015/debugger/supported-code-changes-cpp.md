---
title: Alterações de código com suporte (C++) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue, limitations
- supported code changes
- object files, limitations of Edit and Continue
- C++ language, supported code changes
- coding, supported code changes
- resource files, limitations of Edit and Continue
- code changes, handling in Edit and Continue
- what's new [C++], supported code changes
- code changes
ms.assetid: f5754363-8a56-417b-b904-b05d9dd26d03
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f167b3e9d27145284defa2ff491bb9ce0085f2a3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684908"
---
# <a name="supported-code-changes-c"></a>Alterações de código suportadas (C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editar e continuar para Visual C++ manipula a maioria dos tipos de alterações de código. Porém, algumas alterações não podem ser aplicadas durante a execução do programa. Para aplicar essas alterações sem suporte, você deverá parar a execução e criar uma versão atualizada do código.  
  
 Consulte [Editar e continuar (Visual C++)](../debugger/edit-and-continue-visual-cpp.md) para obter informações sobre como trabalhar com editar e continuar para C++ no Visual Studio.  
  
## <a name="unsupported-changes"></a><a name="BKMK_Unsupported_changes"></a> Alterações sem suporte  

As seguintes alterações de C/C++ não podem ser aplicadas durante uma sessão de depuração:  
  
- A maioria das alterações aos dados globais ou estáticos.  
  
- As alterações nos executáveis que são copiados de outro computador e não são criados localmente.  
  
- As alterações para um tipo de dados que afeta o layout de um objeto, como, por exemplo, membros de dados de uma classe.  
  
- Adicionando mais de 64k bytes do novo código ou dados.  
  
- Adicionando variáveis que exigem um construtor em um ponto antes do ponteiro de instrução.  
  
- As alterações que afetam o código que exigem a inicialização de tempo de execução.  
  
- Adicionar manipuladores de exceção, em alguns casos.  
  
- Alterações aos arquivos de recurso.  
  
- Alterações ao código em arquivos somente leitura.  
  
- Alterações ao código sem um arquivo PDB correspondente.  
  
- Alterações ao código que não tem arquivo de objeto.  
  
Se você executar uma destas alterações e tentar aplicar alterações de código, um erro ou uma mensagem de aviso serão exibidos na janela de **Saída**.  
  
- Editar e Continuar não atualiza bibliotecas estáticas. Se você fizer uma alteração em uma biblioteca estática, a execução continuará com a versão antiga e nenhum aviso será emitido.  
  
## <a name="unsupported-scenarios"></a><a name="BKMK_Unsupported_scenarios"></a> Cenários sem suporte  
 Editar e Continuar para C/C++ está indisponível nos seguintes cenários de depuração:  
  
- Depurando aplicativos nativos compilados com [/zo (aprimorar a depuração otimizada)](https://msdn.microsoft.com/library/eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f)  
  
- Em versões do Visual Studio anteriores ao Visual Studio 2015 atualização 1, depuração de aplicativos ou componentes da Windows Store. A partir do Visual Studio 2015 atualização 1, você pode usar editar e continuar em aplicativos C++ do Windows Store e aplicativos do DirectX, pois ele agora dá suporte à `/ZI` opção de compilador com a  `/bigobj` opção. Você também pode usar editar e continuar com binários compilados com a `/FASTLINK` opção.  
  
- Depuração no Windows 98.  
  
- Depuração de modo misto (nativo/gerenciado).  
  
- Depuração de JavaScript.  
  
- Depuração de SQL.  
  
- Depurando um arquivo de despejo.  
  
- Editando o código após uma exceção sem tratamento quando a opção **Desenrolar a pilha de chamadas em exceções não tratadas** não está selecionada.  
  
- Depurando um aplicativo usando **Attach to** em vez de executar o aplicativo escolhendo **Iniciar** no menu **depurar** .  
  
- Depurando código otimizado.  
  
- Depurando uma versão antiga do código depois que uma nova versão não é compilada devido a erros de compilação.  
  
## <a name="linking-limitations"></a><a name="BKMK_Linking_limitations"></a> Limitações de vinculação  
  
### <a name="linker-options-that-disable-edit-and-continue"></a><a name="BKMK_Linker_options_that_disable_Edit_and_Continue"></a> Opções de vinculador que desabilitam Editar e Continuar  
 As opções de vinculador a seguir desabilitam Editar e Continuar:  
  
- Setting **/OPT: REF**, **/OPT: ICF**ou **/incremental: não** desabilita Edit and Continue com o seguinte aviso:  
  
     LINK : warning LNK4075: ignoring /EDITANDCONTINUE due to /OPT  
  
     especificação  
  
- Definir **/Order**, **/Release**ou **/Force** desabilita editar e continuar com este aviso:  
  
     LINK : warning LNK4075: ignoring /INCREMENTAL due to /option  
  
     especificação  
  
- Definir qualquer opção que evite a criação de um arquivo de banco de dados do programa (.pdb) desabilita Editar e Continuar sem aviso específico.  
  
### <a name="auto-relinking-limitations"></a><a name="BKMK_Auto_relinking_limitations"></a> Limitações de revinculação automática  
 Por padrão, Editar e Continuar vincula novamente o programa ao final de uma sessão de depuração para criar um executável atualizado.  
  
 Editar e Continuar não pode vincular o programa novamente se você o depurá-lo a partir de um local diferente do local de compilação original. Uma mensagem informa que você precisa recompilar manualmente.  
  
 Editar e Continuar não recompila bibliotecas estáticas. Se você fizer alterações em uma biblioteca estática usando editar e continuar, será necessário recriar manualmente a biblioteca e vincular novamente os aplicativos que o utilizam.  
  
 Editar e Continuar não invoca as etapas personalizadas de compilação. Se o seu programa usa etapas personalizadas de compilação, recompile manualmente de modo que as etapas personalizadas de compilação possam ser invocadas. Nesse caso, você pode desabilitar nova vinculação após Editar e Continuar para assegurar que seja solicitado a fazer a recompilação manualmente.  
  
 **Para desabilitar a nova vinculação após Editar e Continuar**  
  
1. No menu de **Depurar**, escolha **Opções e Configurações**.  
  
2. Na caixa de diálogo **Opções** , no nó **depuração** e selecione o nó **Editar e continuar** .  
  
3. Desmarque a caixa de seleção **Vincular novamente alterações de código após a depuração**.  
  
## <a name="precompiled-header-limitations"></a><a name="BKMK_Precompiled_Header_Limitations"></a> Limitações de cabeçalho pré-compilado  
 Por padrão, Editar e Continuar carrega e processa cabeçalhos pré-compilados no plano de fundo para acelerar o processamento de alterações de código. O carregamento de cabeçalhos pré-compilados requer a alocação de memória física, o que pode ser um problema se você estiver compilando em um computador com RAM limitada. Você pode determinar se isso pode ser um problema usando o Gerenciador de tarefas do Windows para determinar a quantidade de memória física disponível durante a depuração. Se esse valor for maior que o tamanho dos cabeçalhos pré-compilados, Editar e Continuar não terá problemas. Se o valor for menor que o tamanho dos cabeçalhos pré-compilados, você pode impedir que Editar e Continuar carregue cabeçalhos pré-compilados no plano de fundo.  
  
 **Para desabilitar o carregamento em segundo plano de cabeçalhos pré-compilados para Editar e Continuar**  
  
1. No menu de **Depurar**, escolha **Opções e Configurações**.  
  
2. Na caixa de diálogo **Opções** , no nó **depuração** e selecione o nó **Editar e continuar** .  
  
3. Desmarque a caixa de seleção **Permitir Pré-Compilação**.  
  
## <a name="idl-attribute-limitations"></a><a name="BKMK_IDL_Attribute_Limitations"></a> Limitações de atributo IDL  
 Editar e Continuar não regeneram arquivos IDL (definição da interface). Consequentemente, as alterações aos atributos de IDL não serão refletidas ao depurar. Para ver o resultado das alterações em atributos IDL, você deve parar a depuração e recompilar seu aplicativo. Editar e Continuar não gera um erro ou um aviso se os atributos de IDL tiverem sido alterados. Para obter mais informações, confira [Atributos de IDL](https://msdn.microsoft.com/library/04c596f4-c97b-4952-8053-316678b1d0b6).  
  
## <a name="see-also"></a>Consulte Também  
 [Editar e continuar (Visual C++)](../debugger/edit-and-continue-visual-cpp.md)
