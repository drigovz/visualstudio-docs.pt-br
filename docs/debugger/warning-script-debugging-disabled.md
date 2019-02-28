---
title: 'Aviso: Depuração de Script desabilitada | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.scriptdisabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 323d2b1d-52a4-42f7-b4ad-96b4b0c23b8d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2543ad00b2065f7659a89e165c2d4df990403667
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56687036"
---
# <a name="warning-script-debugging-disabled"></a>Aviso: depuração de script desabilitada
A depuração de scripts está atualmente desabilitada no Internet Explorer

 Esse aviso ocorre quando você tenta depurar o script sem habilitar a depuração de scripts no Internet Explorer. Por razões de segurança, o Internet Explorer desabilita a depuração de scripts por padrão.

### <a name="to-enable-script-debugging-in-internet-explorer"></a>Para habilitar a depuração de scripts no Internet Explorer

1.  No menu do Internet Explorer **Ferramentas**, escolha **Opções da Internet**.

2.  Na caixa de diálogo **Opções da Internet** , clique na guia **Avançado** .

3.  Na guia **Avançado**, examine a caixa **Configurações**, categoria **Navegação**.

4.  Limpe **Desabilitar depuração de scripts (Internet Explorer)**.

5.  Clique em **OK**.

6.  Encerre e reinicie o Internet Explorer.

     As novas configurações serão aplicadas.

## <a name="see-also"></a>Consulte também
- [Como anexar ao script](../debugger/how-to-attach-to-script.md)