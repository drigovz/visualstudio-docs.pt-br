---
title: 'Aviso: Depuração de script desabilitada | Microsoft Docs'
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
ms.openlocfilehash: 50fe457e2b66a4c1ddafc9fc24658f58f6f753d2
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60114634"
---
# <a name="warning-script-debugging-disabled"></a>Aviso: Depuração de script desabilitada
A depuração de scripts está atualmente desabilitada no Internet Explorer

 Esse aviso ocorre quando você tenta depurar o script sem habilitar a depuração de scripts no Internet Explorer. Por razões de segurança, o Internet Explorer desabilita a depuração de scripts por padrão.

### <a name="to-enable-script-debugging-in-internet-explorer"></a>Para habilitar a depuração de scripts no Internet Explorer

1. No menu do Internet Explorer **Ferramentas**, escolha **Opções da Internet**.

2. Na caixa de diálogo **Opções da Internet** , clique na guia **Avançado** .

3. Na guia **Avançado**, examine a caixa **Configurações**, categoria **Navegação**.

4. Limpe **Desabilitar depuração de scripts (Internet Explorer)**.

5. Clique em **OK**.

6. Encerre e reinicie o Internet Explorer.

     As novas configurações serão aplicadas.

## <a name="see-also"></a>Consulte também
- [Como: Anexar ao script](../debugger/how-to-attach-to-script.md)