---
title: 'Como: Usar a janela registros | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.registers
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- registers, debugging
- register contents
- flags, Registers window
- register groups
- debugging [Visual Studio], Registers window
- Registers window
ms.assetid: 2918ffa2-562f-40d6-9053-ef321bbeb767
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 233092af638824c462a6d9a47865a1c6f5fd9397
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697461"
---
# <a name="how-to-use-the-registers-window"></a>Como: Usar a janela registros
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A janela registros estará disponível somente se a depuração do nível de endereços estiver habilitada na **opções** caixa de diálogo **depuração** nó **geral** categoria.  
  
 O **registra** janela exibe conteúdo do registro. Se você mantiver os **registra** janela aberta, conforme você percorre seu programa, você pode ver alteração dos valores do registro como o código é executado. Os valores que foram alterados recentemente são exibidos em vermelho. Você pode editar valores do registro. Para obter mais informações, confira [Como: Editar um valor de registro](../debugger/how-to-edit-a-register-value.md).  
  
 Para reduzir a desordem, a janela **Registros** organiza registros em grupos, que variam de acordo com a plataforma e o tipo de processador. Você pode exibir ou ocultar grupos como desejar. Para obter mais informações, confira [Como: Exibir e ocultar grupos de registros](../debugger/how-to-display-and-hide-register-groups.md).  
  
 Para obter uma introdução de alto nível para conceitos por trás de registros e a janela registros, consulte [Noções básicas de depuração: Janela de registros](../debugger/debugging-basics-registers-window.md).  
  
> [!NOTE]
> As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-the-registers-window"></a>Para exibir a janela Registros  
  
- Sobre o **Debug** menu, escolha **Windows**e, em seguida, escolha **registra**.  
  
     O depurador deve estar em execução ou no modo de interrupção.  
  
    > [!NOTE]
    > As informações de registro não estão disponíveis para scripts ou aplicativos SQL.  
  
## <a name="see-also"></a>Consulte também  
 [Noções básicas de depuração: Janela registros](../debugger/debugging-basics-registers-window.md)   
 [Exibindo dados no depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Noções básicas de depuração: janela Registros](../debugger/debugging-basics-registers-window.md)
