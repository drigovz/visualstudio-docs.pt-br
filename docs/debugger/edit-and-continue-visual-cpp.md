---
title: Editar e continuar (C++) | Microsoft Docs
ms.date: 05/31/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C++]
- debugging [C++], Edit and Continue
- C/C++, Edit and Continue
ms.assetid: 1815251e-a877-433e-9e5e-69bd9ba254c7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: c2d92477e37b4918e0601bf163e07f5a8492136c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72737906"
---
# <a name="edit-and-continue-c"></a>Editar e continuar (C++)
Você pode usar editar e continuar em projetos C++. Consulte [alterações de código com suporte (C++)](../debugger/supported-code-changes-cpp.md) para obter informações sobre as limitações de editar e continuar.

Para obter mais informações sobre os aprimoramentos do Visual Studio 2015 atualização 3, consulte [C++ Edit and Continue no Visual Studio 2015 Update 3](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/).

 A opção de compilador [/zo (aprimorar a depuração otimizada)](/cpp/build/reference/zo-enhance-optimized-debugging) que foi introduzida no Visual Studio 2013 atualização 3 adiciona informações adicionais aos arquivos. PDB (símbolo) para binários compilados sem a opção [/OD (Disable (debug))](https://msdn.microsoft.com/library/aafb762y.aspx) .

 **/Zo** desabilita editar e continuar. Consulte [como: depurar código otimizado](../debugger/how-to-debug-optimized-code.md).

## <a name="enable-or-disable-edit-and-continue"></a><a name="BKMK_Enable_or_disable_automatic_invocation_of_Edit_and_Continue"></a> Habilitar ou desabilitar editar e continuar
 Talvez você queira desabilitar a invocação automática de editar e continuar se estiver fazendo edições no código que não deseja aplicar durante a sessão de depuração atual. Você também pode reabilitar a edição e continuar automaticamente.

> [!IMPORTANT]
> Para obter as configurações de compilação necessárias e outras informações sobre compatibilidade de recursos, consulte [C++ Edit and Continue no Visual Studio 2015 atualização 3](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/).

1. Se você estiver em uma sessão de depuração, pare a depuração (**Shift + F5**).

2. No menu **Ferramentas**, escolha **Opções**.

3. Na caixa de diálogo **Opções** , selecione **depuração > geral**.

4. Para habilitar, selecione **habilitar editar e continuar**. Para desabilitar, desmarque a caixa de seleção.

5. No grupo **Editar e continuar** , marque ou desmarque a caixa de seleção **habilitar editar e continuar nativo** .

   Alterar essa configuração afeta todos os projetos nos quais você trabalha. Você não precisa recriar seu aplicativo após alterar essa configuração. Se você criar seu aplicativo a partir da linha de comando ou de um makefile, mas você depurar no ambiente do Visual Studio, ainda poderá usar editar e continuar se você definir a opção **/Zi** .

## <a name="how-to-apply-code-changes-explicitly"></a><a name="BKMK_How_to_apply_code_changes_explicitly"></a> Como aplicar alterações no código de forma explícita
 Em C++, editar e continuar pode aplicar alterações de código de duas maneiras. As alterações de código podem ser aplicadas implicitamente, quando você escolhe um comando de execução ou explicitamente usando o comando **Aplicar Alterações de Código**.

 Quando você aplica as alterações de código explicitamente, o programa permanece no modo de interrupção – nenhuma execução ocorre.

- Para aplicar alterações de código explicitamente, no menu **depurar** , escolha **aplicar alterações de código**.

## <a name="how-to-stop-code-changes"></a><a name="BKMK_How_to_stop_code_changes"></a> Como parar as alterações de código
 Quando Editar e Continuar estiver no processo de aplicar alterações de código, você poderá interromper a operação.

 Para parar de aplicar alterações de código:

- No menu **depurar** , escolha **parar de aplicar alterações de código**.

  Este item de menu está visível apenas quando as alterações de código estão sendo aplicadas.

  Se você escolher esta opção, nenhuma das alterações de código serão confirmadas.

## <a name="how-to-reset-the-point-of-execution"></a><a name="BKMK_How_to_reset_the_point_of_execution"></a> Como redefinir o ponto de execução
 Algumas alterações de código podem fazer o ponto de execução ser movido para um novo local quando Editar e Continuar aplicar as alterações. Editar e Continuar coloca o ponto de execução o mais exatamente possível, mas os resultados podem não estar corretos em todos os casos.

 No C++, uma caixa de diálogo informa quando o ponto de execução é alterado. Você deve verificar se o local está correto antes de continuar a depuração. Se não estiver correta, use o comando **Definir Próxima Instrução**. Para obter mais informações, consulte [definir a próxima instrução a ser executada](https://msdn.microsoft.com/library/y740d9d3.aspx#BKMK_Set_the_next_statement_to_execute).

## <a name="how-to-work-with-stale-code"></a><a name="BKMK_How_to_work_with_stale_code"></a> Como trabalhar com código obsoleto
 Em alguns casos, Editar e Continuar não pode aplicar imediatamente alterações de código ao executável, mas talvez consiga aplicá-las posteriormente se você continuar a depuração. Isso ocorre se você editar uma função que chama a função atual ou se adicionar mais de 64 bytes de novas variáveis a uma função na pilha de chamadas

 Nesses casos, o depurador continua executando o código original até que as alterações possam ser aplicadas. O código obsoleto aparece como uma janela temporária do arquivo de origem em uma janela separada de origem, com um título como, por exemplo, `enc25.tmp`. A origem editada continuará aparecendo na janela do original. Se você tentar editar o código obsoleto, será exibida uma mensagem de aviso.

## <a name="see-also"></a>Confira também
- [Alterações de código com suporte (C++)](../debugger/supported-code-changes-cpp.md)