---
title: Suporte a site | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f1a96504783de466551c6fb9d055b95ba38df760
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687689"
---
# <a name="web-site-support"></a>Suporte a site
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Um sistema de projeto de site é um sistema de projeto que cria projetos Web. Os projetos da Web, por sua vez, criam aplicativos Web. Um projeto de site gera um arquivo executável para cada página da Web com código associado. Arquivos executáveis adicionais são gerados a partir dos arquivos de código-fonte na pasta/App_Code.  
  
 Os sistemas de projeto de site são criados adicionando modelos e atributos de registro a um sistema de projeto existente. Um desses atributos seleciona o provedor IntelliSense para o idioma. A implementação do provedor do IntelliSense manipula referências e chama o compilador de linguagem quando uma página da Web inteligente que não é armazenada em cache é solicitada.  
  
 O compilador de linguagem usado para compilar páginas da Web deve ser registrado com [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] . Você pode usar o [ \<compiler> elemento](https://msdn.microsoft.com/library/7a151659-b803-4c27-b5ce-1c4aa0d5a823) em um arquivo de Web.config para registrar o compilador, como no exemplo a seguir:  
  
```  
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>  
```  
  
## <a name="in-this-section"></a>Nesta seção  
 [Modelos de suporte a site](../../extensibility/internals/web-site-support-templates.md)  
 Lista os modelos que você pode usar para criar novos projetos de site e itens associados.  
  
 [Atributos de suporte a site](../../extensibility/internals/web-site-support-attributes.md)  
 Apresenta os atributos de registro que conectam um projeto de site ao [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] e ao [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] .  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Projetos Web](../../extensibility/internals/web-projects.md)  
 Apresenta uma visão geral dos dois tipos de projetos da Web, projetos de sites e projetos de aplicativos Web.
