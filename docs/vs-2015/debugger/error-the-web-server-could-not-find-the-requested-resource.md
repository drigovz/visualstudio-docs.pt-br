---
title: 'Erro: O servidor Web não foi possível encontrar o recurso solicitado | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 1ceeaf30-918c-42bb-ace1-96944530fef3
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 656ebd6f8b1e720afd129bca3d53712526fc914f
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "59000058"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>Erro: O servidor Web não conseguiu localizar o recurso solicitado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Devido aos critérios de segurança, o IIS retornou um erro genérico.  
  
 Uma das possíveis causas é a configuração de segurança do servidor. O IIS 6.0 e versões anteriores usaram um programa complementar, conhecido como URLScan, para filtrar solicitações suspeitas e malformadas. O IIS 7.0 tem a Filtragem de Solicitações incorporada pelo mesmo motivo. Em ambos os casos, a filtragem demasiadamente restritiva pode impedir que o Visual Studio depure o servidor.  
  
 Há várias causas possíveis para esse erro. Algumas das causas mais comuns incluem um problema com a instalação ou a configuração do IIS, a configuração do site ou permissões no sistema de arquivos. Você pode tentar acessar o recurso com um navegador. Dependendo de como o IIS é configurado, você pode ter que usar um navegador local no servidor ou inspecionar o log de erros do IIS para obter uma mensagem de erro detalhada.  
  
 Para obter mais informações sobre como solucionar problemas do IIS, confira [Gerenciamento e administração do IIS](http://go.microsoft.com/fwlink/?LinkId=255872).  
  
## <a name="see-also"></a>Consulte também  
 [Ferramenta de segurança UrlScan](https://www.iis.net/downloads/microsoft/urlscan)   
 [Erro: O servidor Web foi bloqueado e está bloqueando o verbo DEBUG](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)
