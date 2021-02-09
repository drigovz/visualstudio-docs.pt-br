---
title: Ocorreu um erro de DCOM durante a tentativa de contatar o computador remoto. O acesso foi negado.
titleSuffix: ''
description: "' Ocorreu um erro DCOM ao tentar contatar o computador remoto. Acesso negado. ' Exibir informações sobre esta referência de erro de depuração remota do Visual Studio."
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.remote.dcom_access_denied
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, DCOM error
- remote DCOM access denied error
- DCOM, access errors
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4e4c33065feff6b4a2a0d3e292004b51fda744cf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858027"
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>Ocorreu um erro de DCOM durante a tentativa de contatar o computador remoto. O acesso foi negado.
A depuração remota usa DCOM para se comunicar entre os computadores locais e remotos nas seguintes situações:

- O depurador é definido como **modo de compatibilidade nativo** ou o **modo de compatibilidade gerenciado** é verificado na página **ferramentas > opções > depuração**

- Você está depurando o código C++ (C++/CLI) gerenciado.

- No Visual Studio 2013, quando **habilitar a opção Editar e continuar nativo** é verificado na página **ferramentas > opções > depuração**

- Alguns cenários de depuração de terceiros

  Esse erro ocorre quando o processo do Visual Studio não puder se autenticar (ou as credenciais fornecidas forem julgadas insuficientes) para o processo remoto do depurador sobre DCOM. Uma ou mais das seguintes alternativas podem resolver o problema:

- Desative o modo de  **compatibilidade nativa** e o **modo de compatibilidade gerenciado**.

- Em Visual Studio 2013, desative **Habilitar edição e continuar nativo**.

- Reinicializar ambos os computadores.

- Se a depuração remota exigir a inserção de credenciais, verifique a opção para salvar as credenciais.

## <a name="see-also"></a>Consulte também

- [Erros de depuração remota e solução de problemas](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Depuração remota](../debugger/remote-debugging.md)