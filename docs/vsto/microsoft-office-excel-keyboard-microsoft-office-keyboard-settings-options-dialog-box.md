---
title: Caixa de diálogo de opções de teclado do Excel do Microsoft Office, configurações de teclado do Microsoft Office,
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: db76d40db1038983cd756c5eb35549357afa53c3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53926470"
---
# <a name="microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Caixa de diálogo de opções de teclado do Excel do Microsoft Office, configurações de teclado do Microsoft Office,
  Microsoft Office Excel e Visual Studio ambos lidam com teclas de atalho. Comandos diferentes no Excel e no Visual Studio pode representar a mesma combinação de teclas de atalho. Quando o Excel está aberto em um projeto de nível de documento no Visual Studio, o aplicativo apenas uma por vez recebe os comandos de tecla de atalho. Por padrão, o Visual Studio recebe todos os comandos de tecla de atalho, mas você pode fazer com que o Excel recebê-las quando o documento tem o foco, selecionando **esquema de teclado dinâmico**.  
  
 Se você usar uma tecla de atalho que não está atribuída a um comando no aplicativo que atualmente está tratando as teclas de atalho, a tecla de atalho é passada para o outro aplicativo.  
  
 A opção que você selecione permanecerá em vigor para projetos do Excel até você alterá-lo. A seleção não afeta seus projetos do Microsoft Office Word; Você deve fazer qualquer alteração para o Word usando as opções de teclado do Microsoft Office Word.  
  
## <a name="uielement-list"></a>Lista UIElement  
 **Esquema de teclado do Visual Studio**  
 Visual Studio recebe todos os comandos de tecla de atalho, mesmo que o Excel tem o foco. Por exemplo, se você pressionar a tecla de função **F5** enquanto o Excel tem o foco, o Visual Studio inicia a depuração de sua solução.  
  
 **Esquema de teclado dinâmico**  
 Visual Studio recebe comandos de tecla de atalho somente quando ele tem o foco. Quando o Excel tem o foco, o Excel recebe todos os comandos de tecla de atalho. Por exemplo, se você pressionar a tecla de função **F5** enquanto o Excel tem o foco, o Excel abre o **ir para** caixa de diálogo. Se você pressionar **F5** enquanto o Visual Studio tem o foco, o Visual Studio inicia a depuração de sua solução.  
  
## <a name="see-also"></a>Consulte também  
 [Caixa de diálogo de opções de teclado do Word do Microsoft Office, configurações de teclado do Microsoft Office,](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
