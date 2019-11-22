---
title: Editar e continuar (Visual C++) | Microsoft Docs
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
- Edit and Continue [C++]
- debugging [C++], Edit and Continue
- C/C++, Edit and Continue
ms.assetid: 1815251e-a877-433e-9e5e-69bd9ba254c7
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fef02f08ac635687eaaf071188ba0455c6389d9e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301057"
---
# <a name="edit-and-continue-visual-c"></a>Editar e continuar (Visual C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode usar editar e continuar em projetos C++ visuais. Consulte [alterações de código comC++suporte ()](../debugger/supported-code-changes-cpp.md) para obter informações sobre as limitações de editar e continuar.  
  
 A partir do Visual Studio 2015 atualização 1, agora você pode usar editar e continuar em aplicativos C++ da Windows Store e aplicativos do DirectX, pois ele agora dá suporte à opção de compilador **/Zi** com a opção **/bigobj** . Você também pode usar editar e continuar com binários compilados com a opção **/FASTLINK**  
  
 Outros aprimoramentos da atualização 1 incluem uma caixa de diálogo de espera New, cancelável e notificação quando um arquivo não dá suporte a editar e continuar. Para obter mais informações sobre melhorias da atualização 1, consulte [melhorias C++ para editar e continuar no Visual Studio 2015 atualização 1](https://devblogs.microsoft.com/cppblog/improvements-for-c-edit-and-continue-in-visual-studio-2015-update-1/).  
  
 A opção de compilador [/zo (aprimorar a depuração otimizada)](https://msdn.microsoft.com/library/eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f) que foi introduzida no Visual Studio 2013 atualização 3 adiciona informações adicionais aos arquivos. PDB (símbolo) para binários compilados sem a opção [/OD (Disable (debug))](https://msdn.microsoft.com/library/aafb762y.aspx) .  
  
 **/Zo** desabilita editar e continuar. Consulte [como: depurar código otimizado](../debugger/how-to-debug-optimized-code.md).  
  
## <a name="BKMK_Enable_or_disable_automatic_invocation_of_Edit_and_Continue"></a>Habilitar ou desabilitar editar e continuar  
 Talvez você queira desabilitar a invocação automática de editar e continuar se estiver fazendo edições no código que não deseja aplicar durante a sessão de depuração atual. Você também pode reabilitar a edição e continuar automaticamente.  
  
1. No menu **Ferramentas**, escolha **Opções**.  
  
2. Na caixa de diálogo **Opções** , selecione **depuração/geral**.  
  
3. No grupo **Editar e continuar** , marque ou desmarque a caixa de seleção **habilitar editar e continuar nativo** .  
  
   Alterar essa configuração afeta todos os projetos nos quais você trabalha. Você não precisa recriar seu aplicativo após alterar essa configuração. Você pode alterar a configuração mesmo enquanto estiver depurando. Se você criar seu aplicativo a partir da linha de comando ou de um makefile, mas você depurar no ambiente do Visual Studio, ainda poderá usar editar e continuar se você definir a opção **/Zi** .  
  
## <a name="BKMK_How_to_apply_code_changes_explicitly"></a> Como aplicar alterações no código de forma explícita  
 No Visual C++, editar e continuar pode aplicar alterações de código de duas maneiras. As alterações de código podem ser aplicadas implicitamente, quando você escolhe um comando de execução ou explicitamente usando o comando **Aplicar Alterações de Código**.  
  
 Quando você aplica as alterações de código explicitamente, o programa permanece no modo de interrupção – nenhuma execução ocorre.  
  
- Para aplicar alterações de código explicitamente, no menu **depurar** , escolha **aplicar alterações de código**.  
  
## <a name="BKMK_How_to_stop_code_changes"></a> Como parar as alterações de código  
 Quando Editar e Continuar estiver no processo de aplicar alterações de código, você poderá interromper a operação.  
  
 Para parar de aplicar alterações de código:  
  
- No menu **depurar** , escolha **parar de aplicar alterações de código**.  
  
  Este item de menu está visível apenas quando as alterações de código estão sendo aplicadas.  
  
  Se você escolher esta opção, nenhuma das alterações de código serão confirmadas.  
  
## <a name="BKMK_How_to_reset_the_point_of_execution"></a>Como redefinir o ponto de execução  
 Algumas alterações de código podem fazer o ponto de execução ser movido para um novo local quando Editar e Continuar aplicar as alterações. Editar e Continuar coloca o ponto de execução o mais exatamente possível, mas os resultados podem não estar corretos em todos os casos.  
  
 No Visual C++, uma caixa de diálogo informa quando o ponto de execução é alterado. Você deve verificar se o local está correto antes de continuar a depuração. Se não estiver correta, use o comando **Definir Próxima Instrução**. Para obter mais informações, consulte [definir a próxima instrução a ser executada](https://msdn.microsoft.com/library/y740d9d3.aspx#BKMK_Set_the_next_statement_to_execute).  
  
## <a name="BKMK_How_to_work_with_stale_code"></a> Como trabalhar com código obsoleto  
 Em alguns casos, Editar e Continuar não pode aplicar imediatamente alterações de código ao executável, mas talvez consiga aplicá-las posteriormente se você continuar a depuração. Isso ocorre se você editar uma função que chama a função atual ou se adicionar mais de 64 bytes de novas variáveis a uma função na pilha de chamadas  
  
 Nesses casos, o depurador continua executando o código original até que as alterações possam ser aplicadas. O código obsoleto aparece como uma janela temporária do arquivo de origem em uma janela separada de origem, com um título como, por exemplo, `enc25.tmp`. A origem editada continuará aparecendo na janela do original. Se você tentar editar o código obsoleto, será exibida uma mensagem de aviso.  
  
## <a name="see-also"></a>Consulte também  
 [Alterações de código com suporte (C++)](../debugger/supported-code-changes-cpp.md)
