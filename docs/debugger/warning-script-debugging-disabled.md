---
title: 'Aviso: depuração de script desabilitada | Microsoft Docs'
description: Um aviso de "depuração de script desabilitado" ocorre quando você tenta Depurar o script sem habilitar a depuração de script no Internet Explorer. Consulte as etapas para habilitá-lo.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 7cc2e03a4efcf9a88675fd3c80f374ff78ba35bb
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149554"
---
# <a name="warning-script-debugging-disabled"></a>Aviso: depuração de script desabilitada
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

## <a name="see-also"></a>Confira também
- [Como: anexar ao script](attach-to-running-processes-with-the-visual-studio-debugger.md)