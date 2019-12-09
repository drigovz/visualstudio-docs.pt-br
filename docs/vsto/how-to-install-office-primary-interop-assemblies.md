---
title: 'Como: Instalar assemblies de interoperabilidade primária do Office'
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies [Office development in Visual Studio], installing
- Office primary interop assemblies, installing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ee6755a2d795d2018136785986a5a346ddc07dc6
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551800"
---
# <a name="how-to-install-office-primary-interop-assemblies"></a>Como: Instalar assemblies de interoperabilidade primária do Office
  Instale os assemblies de interoperabilidade primária (PIAs) do Microsoft Office ao instalar o Office.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-install-the-pias-when-you-install-office"></a>Para instalar os PIAs ao instalar o Office

1. Certifique-se de que você tenha uma versão do .NET Framework 2.0 ou posterior.

2. Instale o Microsoft Office e certifique-se de que o recurso de **suporte de programação .net** esteja selecionado para os aplicativos que você deseja estender (esse recurso está incluído na instalação padrão).

    > [!WARNING]
    > Por padrão, o PIA é inserido em sua solução quando você o cria para que você não precise distribuir PIAs aos usuários como um pré-requisito para usar seu suplemento ou personalização do VSTO.

## <a name="see-also"></a>Consulte também
- [Assemblies de interoperabilidade primária do Office](../vsto/office-primary-interop-assemblies.md)
- [Como: Direcionar aplicativos do Office por meio de assemblies de interoperabilidade primária](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Como: Configurar um computador para desenvolver soluções do Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Como: Instalar o Ferramentas do Visual Studio para o Office Runtime Redistributable](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Visão geral &#40;do desenvolvimento de soluções do Office VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Introdução &#40;ao desenvolvimento do Office no Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
