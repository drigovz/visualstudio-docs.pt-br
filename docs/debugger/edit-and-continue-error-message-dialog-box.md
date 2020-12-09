---
title: Caixa de diálogo Editar e continuar mensagem de erro | Microsoft Docs
description: Editar e continuar pode relatar que ele não está disponível para as alterações de código. Este artigo fornece possíveis motivos.
ms.custom: SEO-VS-2020
ms.date: 10/15/2018
ms.topic: reference
f1_keywords:
- vs.debug.ENC.SupportedButNotAvailable
- vs.debug.ENC.CannotEditWhileException
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue Error Message dialog box
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ef34889b838e2f7eaa92420eec90db9def57e65
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96862836"
---
# <a name="edit-and-continue-error-message"></a>Mensagem de erro editar e continuar

A caixa de mensagem **Editar e continuar** erro aparece quando você está depurando em uma linguagem de código que dá suporte a editar e continuar, mas editar e continuar não está disponível para as alterações de código feitas. A mensagem de erro fornece uma explicação mais detalhada. Para responder ao diálogo, selecione **OK** para fechar a caixa de diálogo e cancelar a tentativa de edição.

As possíveis razões para essa mensagem de erro incluem:

- Tentando editar o código SQL Server.
- Tentando editar código otimizado. Talvez seja necessário alternar de uma compilação de versão para uma compilação de depuração.
- Tentando editar o código enquanto ele está em execução, em vez de durante a pausa no depurador. Tente [definir um ponto de interrupção](../debugger/using-breakpoints.md)e editar o código enquanto estiver em pausa.
- Tentando editar código gerenciado quando apenas a depuração não gerenciada está habilitada. Editar e continuar não funciona com [depuração de modo misto](../debugger/how-to-debug-in-mixed-mode.md).
- Fazer uma alteração de código que não é suportada pelo Edit and Continue em sua linguagem de programação. Para obter mais informações, consulte artigos sobre [alterações de código com suporte em C#](supported-code-changes-csharp.md), [edições sem suporte no Visual Basic editar e continuar](supported-code-changes-csharp.md)e [alterações de código C++ com suporte](supported-code-changes-cpp.md).
- Tentando editar o código em um aplicativo ao qual você está anexado, em vez de iniciar a depuração no menu **depurar** .
- Tentando editar o código durante a depuração de um despejo de Dr. Watson.
- A tentativa de editar o código após uma exceção sem tratamento ocorre e a opção **desenrolar a pilha de chamadas em exceções sem tratamento** não é selecionada.
- Tentando editar o código durante a depuração de um aplicativo de tempo de execução inserido.
- Tentando editar código gerenciado usando uma versão .NET Framework anterior à 4.5.1 com um destino de aplicativo de 64 bits. Para usar editar e continuar para .NET Framework anteriores ao 4.5.1, defina o destino como **x86** na **\<ProjectName>**  >  **Properties**  >  guia **Compilar** Propriedades, configuração **avançada do compilador** .
- Tentativa de editar código em um assembly que foi modificado durante a depuração e foi recarregado.
- Tentando editar o código em um assembly que não foi carregado.
- Começando a depurar uma versão antiga de um aplicativo, pois a versão mais recente tem erros de compilação.

Para obter mais informações, consulte:
- [Postagem do blog editar e continuar em C++](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/)
- [Alterações de código com suporte (C++)](../debugger/supported-code-changes-cpp.md)
- [Editar e continuar](../debugger/edit-and-continue.md)