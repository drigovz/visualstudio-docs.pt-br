---
title: Suporte ao site | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 22047ad1b0709cefa200656e61f8e0d39ace94c9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703438"
---
# <a name="web-site-support"></a>Suporte a site
Um sistema de projeto de site é um sistema de projetos que cria projetos web. Projetos web, por sua vez, criam aplicativos web. Um projeto de site gera um arquivo executável para cada página da Web que tenha código associado. Arquivos executáveis adicionais são gerados a partir dos arquivos de código-fonte na pasta /App_Code.

 Os sistemas de projetos de sites da Web são criados adicionando modelos e atributos de registro a um sistema de projeto existente. Um desses atributos seleciona o provedor IntelliSense para o idioma. A implementação do provedor IntelliSense lida com referências e chama o compilador de idiomas quando uma página da Web inteligente que não é armazenada em cache é solicitada.

 O compilador de idiomas usado para compilar [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]páginas da Web deve ser registrado com . Você pode usar o [ \<compilador> Element](/dotnet/framework/configure-apps/file-schema/compiler/compiler-element) em um arquivo Web.config para registrar o compilador, como no exemplo a seguir:

```
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>
```

## <a name="in-this-section"></a>Nesta seção
- [Modelos de suporte a site](../../extensibility/internals/web-site-support-templates.md)

 Lista os modelos que você pode usar para criar novos projetos de sites e itens associados.

- [Atributos de suporte a site](../../extensibility/internals/web-site-support-attributes.md)

 Apresenta os atributos de registro [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]conectam um projeto de site à e .

## <a name="related-sections"></a>Seções relacionadas
- [Projetos Web](../../extensibility/internals/web-projects.md)

 Apresenta uma visão geral dos dois tipos de projetos web, projetos de sites e projetos de aplicativos web.
