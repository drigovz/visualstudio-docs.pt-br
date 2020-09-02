---
title: Caixa de diálogo Editar e continuar mensagem de erro | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.ENC.SupportedButNotAvailable
- vs.debug.ENC.CannotEditWhileException
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue Error Message dialog box
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5437ef982309ef8595f08283f2685e93d346e764
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62428260"
---
# <a name="edit-and-continue-error-message-dialog-box"></a>Caixa de diálogo Mensagem de Erro de Editar e Continuar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Essa caixa de diálogo aparece quando você está depurando em uma linguagem que dá suporte a editar e continuar, mas **Editar e continuar** não está disponível para o tipo de alterações de código que você fez. A mensagem de erro dentro da caixa fornece uma explicação mais detalhada. As possíveis razões para ver essa caixa de diálogo incluem:  
  
- Você tentou editar o código gerenciado quando a depuração não gerenciada foi habilitada. Editar e Continuar não funcionam com depuração de modo misto.  
  
- Você tentou editar o código do SQL Server.  
  
- Você tentou editar o código durante a depuração de um despejo do Dr. Watson.  
  
- Você tentou editar o código após uma exceção sem tratamento e a opção "**desenrolar a pilha de chamadas em exceções sem tratamento**" não foi selecionada.  
  
- Você tentou editar o código ao depurar um aplicativo inserido de runtime.  
  
- Você tentou editar o código em um programa que você anexou ao em vez de iniciar no menu **depurar** .  
  
- Você tentou editar o código otimizado.  
  
- Você tentou editar o código gerenciado quando o destino é um aplicativo de 64 bits. Se você desejar usar Editar e Continuar, deve definir o destino como x86. (*Project* **Propriedades**do projeto, guia **Compilar** , configuração **avançada do compilador** .).  
  
- Você tentou editar o código em um assembly que foi modificado durante a depuração e foi recarregado.  
  
- Você tentou editar o código em um assembly que não foi carregado.  
  
- Você iniciou a depuração de uma versão antiga do aplicativo (já que a nova versão tem erros de compilação).  
  
- Você tentou editar o código durante a execução.  
  
## <a name="uielement-list"></a>Lista de elementos de interface do usuário  
 **OK**  
 Saia da caixa de diálogo e cancele a tentativa de edição imediatamente anterior.  
  
## <a name="see-also"></a>Consulte Também  
 [Alterações de código com suporte (C++)](../debugger/supported-code-changes-cpp.md)
