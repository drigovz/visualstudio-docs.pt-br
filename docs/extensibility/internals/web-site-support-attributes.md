---
title: Atributos de suporte do Site da Web | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 076b7aa56ec00fda559bbdfdc8b2b9df2be38816
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62907577"
---
# <a name="web-site-support-attributes"></a>Atributos de suporte a site
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projeto de site pode ser estendido para fornecer suporte para Web linguagens de programação. O idioma deve ser registrado com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para que os modelos de projeto podem aparecer em de **New Web Site** caixa de diálogo quando o idioma é selecionado.

O exemplo de IronPython Studio inclui suporte ao site. O exemplo contém as seguintes classes de atributo para registrar o IronPython como uma linguagem de code-behind para novos projetos da Web.

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 Esse atributo é colocado no projeto de linguagem. Ele adiciona o idioma à lista de idiomas de programação da Web a **linguagem** listar na **New Web Site** caixa de diálogo. Por exemplo, o código a seguir adiciona o IronPython à lista:

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Esse atributo também define o caminho de modelos para apontar para a pasta de modelos. Para obter mais informações sobre o local da pasta de modelos, consulte [modelos de suporte do Site da Web](../../extensibility/internals/web-site-support-templates.md).

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute
 Esse atributo é colocado no projeto de linguagem. Isso permite que o projeto de Site da Web aninhar um tipo de arquivo (relacionado) em outro tipo de arquivo (primário) na **Gerenciador de soluções**.

 Por exemplo, o código a seguir especifica que um arquivo de code-behind do IronPython está relacionado a um arquivo. aspx. Quando uma nova página da Web. aspx é criada em uma solução de site da Web da IronPython, um novo arquivo de origem. py é gerado e aparece como um nó filho da página. aspx.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 Esse atributo é colocado sobre o pacote de idioma do projeto. Ele seleciona o provedor do IntelliSense para o idioma.

 Por exemplo, o código a seguir especifica que uma instância de PythonIntellisenseProvider, que implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>, devem ser criados sob demanda para fornecer serviços de linguagem.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 A implementação de IVsIntellisenseProject trata referências e chama o compilador de linguagem quando uma página da Web com o código é solicitada, mas não é armazenado em cache.

## <a name="see-also"></a>Consulte também
- [Suporte ao site](../../extensibility/internals/web-site-support.md)