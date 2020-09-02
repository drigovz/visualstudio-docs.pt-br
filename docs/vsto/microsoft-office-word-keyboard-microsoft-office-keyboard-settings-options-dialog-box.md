---
title: Teclado do Office Word, configurações de teclado, caixa de diálogo opções
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Word.Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Word_Keyboard
- VST.WordOptions.KeyboardMappingScheme
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
ms.openlocfilehash: 5180aa2f4c5022cedcba2c5377d2ff2ac14ffb28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "66835990"
---
# <a name="microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Microsoft Office o teclado do Word, Microsoft Office configurações do teclado, caixa de diálogo opções
  Microsoft Office o Word e o Visual Studio lidam com teclas de atalho. A mesma combinação de teclas de atalho pode representar comandos diferentes no Word e no Visual Studio. Quando o Word está aberto em um projeto de nível de documento no Visual Studio, somente um aplicativo por vez recebe os comandos de tecla de atalho. Por padrão, o Visual Studio recebe todos os comandos de tecla de atalho, mas você pode fazer com que o Word os receba quando o documento tiver foco, selecionando **esquema de teclado dinâmico**.

 Se você usar uma tecla de atalho que não esteja atribuída a um comando no aplicativo que está manipulando as teclas de atalho no momento, a tecla de atalho será passada para o outro aplicativo.

 A opção selecionada permanecerá em vigor para projetos do Word até você alterá-lo. A seleção não afeta Microsoft Office projetos do Excel; Você deve fazer qualquer alteração no Excel usando as opções de teclado do Microsoft Office Excel.

## <a name="uielement-list"></a>Lista de elementos de interface do usuário
 **Esquema de teclado do Visual Studio** O Visual Studio recebe todos os comandos de tecla de atalho, mesmo que o documento do Word tenha foco. Por exemplo, se você pressionar a tecla de função **F5** enquanto o documento tiver foco, o Visual Studio iniciará a depuração da solução.

 **Esquema de teclado dinâmico** O Visual Studio recebe comandos de tecla de atalho somente quando ele tem foco. Quando o documento do Word tiver foco, o Word receberá todos os comandos de tecla de atalho. Por exemplo, se você pressionar a tecla de função **F5** enquanto o documento do Word tiver foco, o Word abrirá a caixa de diálogo **Localizar e substituir** com a guia **ir para** selecionada. Se você pressionar **F5** enquanto o Visual Studio tiver foco, o Visual Studio começará a depurar sua solução.

## <a name="see-also"></a>Confira também
- [Microsoft Office de teclado do Excel, Microsoft Office configurações de teclado, caixa de diálogo opções](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
