---
title: 'Como: usar a janela de registros | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697461"
---
# <a name="how-to-use-the-registers-window"></a>Como usar a janela Registros
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A janela Registros estará disponível apenas se a depuração do nível de endereços estiver habilitada na caixa de diálogo **Opções**, nó **Depuração**, categoria **Geral**.  
  
 A janela de **registros** exibe conteúdo do registro. Se você mantiver a janela de **registros** aberta enquanto percorre seu programa, poderá ver os valores de registro mudarem conforme o seu código é executado. Os valores que foram alterados recentemente são exibidos em vermelho. Você pode editar valores do registro. Para obter mais informações, consulte [como: editar um valor de registro](../debugger/how-to-edit-a-register-value.md).  
  
 Para reduzir a desordem, a janela **Registros** organiza registros em grupos, que variam de acordo com a plataforma e o tipo de processador. Você pode exibir ou ocultar grupos como desejar. Para obter mais informações, consulte [como exibir e ocultar grupos de registros](../debugger/how-to-display-and-hide-register-groups.md).  
  
 Para obter uma introdução de alto nível aos conceitos por trás de registros e a janela de registros, consulte [noções básicas de depuração: janela de registros](../debugger/debugging-basics-registers-window.md).  
  
> [!NOTE]
> As caixas de diálogo e os comandos de menu encontrados podem diferir daqueles descritos na Ajuda, dependendo das configurações ativas ou edição. Para alterar suas configurações, selecione **Importar e Exportar Configurações** no menu **Ferramentas** . Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-the-registers-window"></a>Para exibir a janela Registros  
  
- No menu **depurar** , escolha **Windows**e, em seguida, selecione **registros**.  
  
     O depurador deve estar em execução ou no modo de interrupção.  
  
    > [!NOTE]
    > As informações de registro não estão disponíveis para scripts ou aplicativos SQL.  
  
## <a name="see-also"></a>Consulte Também  
 [Noções básicas de depuração: janela de registros](../debugger/debugging-basics-registers-window.md)   
 [Exibindo dados no depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Noções básicas sobre depuração: janela Registros](../debugger/debugging-basics-registers-window.md)
