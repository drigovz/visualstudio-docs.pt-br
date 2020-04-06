---
title: Atributos de suporte do site | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef75f99480145475278357a552f3ac74c0289800
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703493"
---
# <a name="web-site-support-attributes"></a>Atributos de suporte a site
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]O projeto do site pode ser estendido para fornecer suporte para linguagens de programação da Web. O idioma deve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] registrar-se com isso para que os modelos de projeto possam aparecer na caixa de diálogo **do Novo Site** quando o idioma for selecionado.

A amostra do IronPython Studio inclui suporte ao site. A amostra contém as seguintes classes de atributos para registrar o IronPython como uma linguagem de código atrás para novos projetos da Web.

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 Este atributo é colocado no projeto de linguagem. Ele adiciona o idioma à lista de linguagens de programação da Web na lista **De idiomas** na caixa de diálogo **Novo Site.** Por exemplo, o código a seguir adiciona IronPython à lista:

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Este atributo também define o caminho dos modelos para apontar para a pasta de modelos. Para obter mais informações sobre a localização da pasta de modelos, consulte [Modelos de suporte do site da Web](../../extensibility/internals/web-site-support-templates.md).

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAtributo
 Este atributo é colocado no projeto de linguagem. Ele permite que o projeto do Site da Web aninhar um tipo de arquivo (relacionado) em outro tipo de arquivo (principal) no **Solution Explorer**.

 Por exemplo, o código a seguir especifica que um arquivo de código IronPython está relacionado a um arquivo .aspx. Quando uma nova página da Web .aspx é criada em uma solução de site do IronPython, um novo arquivo de origem .py é gerado e aparece como um nó filho da página .aspx.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 Este atributo é colocado no pacote do projeto de idioma. Ele seleciona o provedor IntelliSense para o idioma.

 Por exemplo, o código a seguir especifica que uma instância do <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>PythonIntellisenseProvider, que implementa, deve ser criada sob demanda para fornecer serviços de idioma.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 A implementação do IVsIntellisenseProject lida com referências e chama o compilador de idiomas quando uma página da Web com código é solicitada, mas não é armazenada em cache.

## <a name="see-also"></a>Confira também
- [Suporte a site](../../extensibility/internals/web-site-support.md)
