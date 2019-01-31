---
title: 'Erro: O servidor Web não foi possível encontrar o recurso solicitado | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
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
ms.openlocfilehash: cba31527af469b897ae178b6b0f810840b7d9cd2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55035468"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>Erro: O servidor Web não conseguiu localizar o recurso solicitado
Devido aos critérios de segurança, o IIS retornou um erro genérico.  

Uma das possíveis causas é a configuração de segurança do servidor. O IIS 6.0 e versões anteriores usaram um programa complementar, conhecido como URLScan, para filtrar solicitações suspeitas e malformadas. O IIS 7.0 tem a Filtragem de Solicitações incorporada pelo mesmo motivo. Em ambos os casos, a filtragem demasiadamente restritiva pode impedir que o Visual Studio depure o servidor.  

Outra possível causa desse erro é que o serviço W3SVC do IIS não foi iniciado. Verifique se esse serviço foi iniciado (esmaecido) na janela Serviços (*Services. msc*).

Há várias causas possíveis adicionais desse erro. Algumas das causas mais comuns incluem um problema com a instalação ou a configuração do IIS, a configuração do site ou permissões no sistema de arquivos. Você pode tentar acessar o recurso com um navegador. Dependendo de como o IIS é configurado, você pode ter que usar um navegador local no servidor ou inspecionar o log de erros do IIS para obter uma mensagem de erro detalhada.  
  
 Para obter mais informações sobre como solucionar problemas do IIS, confira [Gerenciamento e administração do IIS](/iis/manage/provisioning-and-managing-iis/iis-management-and-administration).  
  
## <a name="see-also"></a>Consulte também  
 [Erro: O servidor Web foi bloqueado e está bloqueando o verbo DEBUG](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)