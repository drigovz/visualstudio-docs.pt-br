---
title: O servidor Web não pôde localizar o recurso solicitado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 21b1a97f93909a06ea9a542f83d4a4349b6f3a20
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871241"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>Erro: o servidor Web não conseguiu localizar o recurso solicitado
Devido aos critérios de segurança, o IIS retornou um erro genérico.

Uma das possíveis causas é a configuração de segurança do servidor. O IIS 6.0 e versões anteriores usaram um programa complementar, conhecido como URLScan, para filtrar solicitações suspeitas e malformadas. O IIS 7.0 tem a Filtragem de Solicitações incorporada pelo mesmo motivo. Em ambos os casos, a filtragem demasiadamente restritiva pode impedir que o Visual Studio depure o servidor.

Outra causa possível desse erro é que o serviço W3SVC para IIS não foi iniciado. Verifique se esse serviço foi iniciado (esmaecido) na janela de serviços (*Services. msc*).

Há várias causas possíveis adicionais desse erro. Algumas das causas mais comuns incluem um problema com a instalação ou a configuração do IIS, a configuração do site ou permissões no sistema de arquivos. Você pode tentar acessar o recurso com um navegador. Dependendo de como o IIS é configurado, você pode ter que usar um navegador local no servidor ou inspecionar o log de erros do IIS para obter uma mensagem de erro detalhada.

 Para obter mais informações sobre como solucionar problemas do IIS, confira [Gerenciamento e administração do IIS](/iis/manage/provisioning-and-managing-iis/iis-management-and-administration).

## <a name="see-also"></a>Confira também
- [Erro: o servidor Web foi bloqueado e está bloqueando o verbo de depuração](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)