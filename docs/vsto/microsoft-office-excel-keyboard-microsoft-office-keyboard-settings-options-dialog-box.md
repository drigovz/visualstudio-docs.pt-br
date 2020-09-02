---
title: Teclado do Office Excel, configurações de teclado, caixa de diálogo opções
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ExcelOptions.KeyboardMappingScheme
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Excel_Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Excel.Keyboard
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- keyboard shortcuts, Office development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 090e943df2b61352c2342218c3c71c8f0e60eaad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "66836032"
---
# <a name="microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Microsoft Office de teclado do Excel, Microsoft Office configurações de teclado, caixa de diálogo opções
  Microsoft Office o Excel e o Visual Studio lidam com teclas de atalho. A mesma combinação de teclas de atalho pode representar comandos diferentes no Excel e no Visual Studio. Quando o Excel é aberto em um projeto de nível de documento no Visual Studio, somente um aplicativo por vez recebe os comandos de tecla de atalho. Por padrão, o Visual Studio recebe todos os comandos de tecla de atalho, mas você pode fazer com que o Excel os receba quando o documento tiver foco, selecionando **esquema de teclado dinâmico**.

 Se você usar uma tecla de atalho que não esteja atribuída a um comando no aplicativo que está manipulando as teclas de atalho no momento, a tecla de atalho será passada para o outro aplicativo.

 A opção selecionada permanecerá em vigor para projetos do Excel até você alterá-lo. A seleção não afeta Microsoft Office projetos do Word; Você deve fazer qualquer alteração para o Word usando as opções de teclado do Microsoft Office Word.

## <a name="uielement-list"></a>Lista de elementos de interface do usuário
 **Esquema de teclado do Visual Studio** O Visual Studio recebe todos os comandos de tecla de atalho, mesmo que o Excel tenha foco. Por exemplo, se você pressionar a tecla de função **F5** enquanto o Excel estiver em foco, o Visual Studio iniciará a depuração da solução.

 **Esquema de teclado dinâmico** O Visual Studio recebe comandos de tecla de atalho somente quando ele tem foco. Quando o Excel tem foco, o Excel recebe todos os comandos de tecla de atalho. Por exemplo, se você pressionar a tecla de função **F5** enquanto o Excel tiver foco, o Excel abrirá a caixa de diálogo **ir para** . Se você pressionar **F5** enquanto o Visual Studio tiver foco, o Visual Studio começará a depurar sua solução.

## <a name="see-also"></a>Confira também
- [Microsoft Office o teclado do Word, Microsoft Office configurações do teclado, caixa de diálogo opções](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
