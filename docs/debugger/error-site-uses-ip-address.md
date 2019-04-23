---
title: 'Erro: Site usa endereço IP | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 468cb2c85be088213bc865122a790408c6c992b6
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60093549"
---
# <a name="error-site-uses-ip-address"></a>Erro: O site usa endereço IP
Esse erro ocorre quando o depurador tenta anexar-se automaticamente a um aplicativo Web que está usando um endereço IP. Isso ocorrerá se você alterar **Identificação do site** para **usar o endereço IP específico** no IIS.

 Para que o anexo automático funcione, você precisará criar o projeto com o endereço IP específico em vez de apenas o nome do computador. Caso contrário, o depurador alterará o nome do computador para localhost, o que causará uma falha ao enviar o verbo de depuração para o IIS.

### <a name="to-correct-this-error"></a>Para corrigir este erro

1. Use a anexação manual em vez disso (no menu depurar, escolha **Anexar ao Processo**).

     —ou—

2. Altere a configuração de **Identificação do site do IIS**.

## <a name="see-also"></a>Consulte também
- [Depurando aplicativos Web: erros e solução de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)