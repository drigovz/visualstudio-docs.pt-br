---
title: Controle glifos (Controle de Fonte VSPackage) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9db1b4542eae293e39cda674fac3eb984aa77d3e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708312"
---
# <a name="glyph-control-source-control-vspackage"></a>Controle de glifos (controle de origem VSPackage)
Parte da integração profunda disponível para o controle de origem VSPackages é a capacidade de exibir seus próprios glifos para indicar o status dos itens sob controle de origem.

## <a name="levels-of-glyph-control"></a>Níveis de controle de glifos
 Um glifo de estado é um ícone que indica o status atual de um item quando exibido, por exemplo, no **Solution Explorer** ou na **Exibição de Classe**. Um controle de origem VSPackage pode exercer dois níveis de controle de glifo. Ele pode limitar a escolha dos glifos a um conjunto predefinido [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de glifos fornecidos pelo IDE, ou pode definir um conjunto personalizado de glifos a serem exibidos.

### <a name="default-set-of-glyphs"></a>Conjunto padrão de glifos
 Para determinar os glifos de estado associados a um item no **Solution Explorer,** um <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>projeto solicita o glifo do estado a partir do controle de origem usando o . Um controle de origem VSPackage pode decidir manter a escolha de glifos limitado a glifos predefinidos fornecidos pelo IDE. Neste caso, o VSPackage repassa uma matriz de valores representando as enumerações de glifos definidas em *vsshell.idl*. Para obter mais informações, consulte <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>. Este é um conjunto predefinido de glifos definidos pelo IDE, como um cadeado para o glifo check-in, e uma marca de verificação para o glifo de check-out.

### <a name="custom-set-of-glyphs"></a>Conjunto personalizado de glifos
 Um controle de origem VSPackage pode usar seus próprios glifos para uma aparência única quando ele é instalado. Quando um novo controle de origem VSPackage estiver ativo, ele deve ser capaz de começar a usar seus próprios glifos, mesmo que um controle de origem anterior VSPackage ainda esteja carregado, mas inativo. Neste modo, o controle de origem VSPackage ainda pode usar os ícones existentes para manter uma aparência consistente com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se ele quiser.

 O <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> serviço suporta uma <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>interface, que o VSPackage pode implementar opcionalmente e que será solicitada pelo IDE. Quando o IDE fizer [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uma solicitação, por sua vez tentará obter essa interface do controle de origem registrado no momento, VSPackage. Se a interface existir no VSPackage registrado, a solicitação do IDE para glifos personalizados será bem sucedida; caso contrário, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] o IDE usa seu conjunto padrão de glifos.

 O <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> método é [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usado para obter uma lista de imagens que mostram vários estados de controle de origem. O controle de origem VSPackage retorna ao IDE uma alça para a lista de imagens para seus glifos personalizados. O IDE faz uma cópia da lista de imagens neste momento e usa-a mais tarde para escolher os glifos para exibir. Se a nova interface não `IVsSccGlyphs::GetCustomGlyphList` for `E_NOTIMPL`suportada ou o método retornar, o IDE obtém seus [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]glifos da lista padrão de glifos fornecidos por .

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>
- <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>
