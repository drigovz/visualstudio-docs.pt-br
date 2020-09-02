---
title: Controle de glifo (VSPackage de controle do código-fonte) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b0960209b67c8d2f111296840119807d95bb2e2d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538415"
---
# <a name="glyph-control-source-control-vspackage"></a>Controle de glifo (VSPackage de controle do código-fonte)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Parte da integração profunda disponível para o VSPackages de controle do código-fonte é a capacidade de exibir seus próprios glifos para indicar o status dos itens sob controle do código-fonte.  
  
## <a name="levels-of-glyph-control"></a>Níveis de controle de glifo  
 Um glifo de estado é um ícone que indica o status atual de um item quando exibido, por exemplo, em **Gerenciador de soluções** ou em **modo de exibição de classe**. Um VSPackage de controle do código-fonte pode exercer dois níveis de controle de glifo. Ele pode limitar a escolha de glifos para um conjunto predefinido de glifos fornecidos pelo [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE ou pode definir um conjunto personalizado de glifos a serem exibidos.  
  
### <a name="default-set-of-glyphs"></a>Conjunto padrão de glifos  
 Para determinar os glifos de estado associados a um item em **Gerenciador de soluções**, um projeto solicita o glifo de estado do controle do código-fonte usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A> . Um VSPackage de controle do código-fonte pode decidir manter a escolha dos glifos limitados a glifos predefinidos fornecidos pelo IDE. Nesse caso, o VSPackage retorna uma matriz de valores que representa as enumerações de glifos que são definidas em VSShell. idl. Para obter mais informações, consulte <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon> . Esse é um conjunto predefinido de glifos definido pelo IDE, como um cadeado para o glifo "checked in" e uma marca de seleção como o glifo "checked out".  
  
### <a name="custom-set-of-glyphs"></a>Conjunto personalizado de glifos  
 Um VSPackage de controle do código-fonte pode usar seus próprios glifos para uma "aparência" exclusiva quando ele é instalado. Quando um novo VSPackage de controle do código-fonte estiver ativo, ele deverá ser capaz de começar a usar seus próprios glifos, mesmo que um controle do código-fonte anterior ainda esteja carregado, mas inativo. Nesse modo, o controle do código-fonte VSPackage ainda pode usar os ícones existentes para manter uma aparência consistente com [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] se escolher.  
  
 O <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> serviço oferece suporte a uma interface, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> , que o VSPackage pode, opcionalmente, implementar e que será solicitado pelo IDE. Quando o IDE faz uma solicitação, por [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sua vez, tentará obter essa interface do controle do código-fonte atualmente registrado VSPackage. Se a interface existir no VSPackage registrado, a solicitação do IDE para glifos personalizados terá sucesso; caso contrário, o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE usa seu conjunto padrão de glifos.  
  
 O <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> método é usado pelo [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] para obter uma lista de imagens mostrando vários Estados de controle do código-fonte. O VSPackage de controle do código-fonte retorna ao identificador do IDE a para a lista de imagens de seus glifos personalizados. O IDE faz uma cópia da lista de imagens neste ponto e a usa posteriormente para escolher os glifos a serem exibidos. Se a nova interface não for suportada ou o `IVsSccGlyphs::GetCustomGlyphList` método retornar E_NOTIMPL, o IDE obterá seus glifos da lista padrão de glifos fornecidos pelo [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="see-also"></a>Consulte Também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>
