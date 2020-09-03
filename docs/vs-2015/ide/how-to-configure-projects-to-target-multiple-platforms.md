---
title: Como configurar projetos para se destinarem a várias plataformas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], targeting platforms
- platforms, changing target platforms
ms.assetid: affa2392-7aed-45ac-9ffa-1d8e0496d590
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bb759faff99b641f24df87f73bc1d3d52b6635cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663553"
---
# <a name="how-to-configure-projects-to-target-multiple-platforms"></a>Como configurar projetos para destinar várias plataformas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fornece uma maneira de uma solução se destinar a várias plataformas ou arquiteturas de CPU ao mesmo tempo. As propriedades para defini-las são acessadas por meio da caixa de diálogo **Configuration Manager**.

## <a name="targeting-a-platform"></a>Destinando-se a uma plataforma
 A caixa de diálogo **Configuration Manager** permite criar e definir configurações e plataformas no nível do projeto e da solução. Cada combinação de destinos e configurações no nível da solução pode ter um conjunto exclusivo de propriedades associadas a ela, permitindo mudar facilmente entre, por exemplo, uma configuração de Versão destinada a uma plataforma [!INCLUDE[vcprx64](../includes/vcprx64-md.md)], uma configuração de versão destinada a uma plataforma x86 e uma configuração de Depuração destinada a uma plataforma x86.

#### <a name="to-set-your-configuration-to-target-a-different-platform"></a>Para definir sua configuração para se destinar a uma plataforma diferente

1. No menu **Compilar**, clique em **Gerenciador de Configurações**.

2. Na **caixa plataforma de solução ativa**, selecione a plataforma que você deseja que sua solução direcione ou selecione **\<New>** para criar uma nova plataforma. O [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] compilará seu aplicativo para se destinar à plataforma definida como a plataforma ativa na caixa de diálogo **Configuration Manager**.

## <a name="removing-a-platform"></a>Removendo uma plataforma
 Se perceber que não precisa de uma plataforma, você pode removê-la usando a caixa de diálogo Configuration Manager. Isso removerá todas as configurações de solução e projeto que você definiu para essa combinação de configuração e destino.

#### <a name="to-remove-a-platform"></a>Para remover uma plataforma

1. No menu **Compilar**, clique em **Gerenciador de Configurações**.

2. Na **caixa plataforma de solução ativa**, selecione **\<Edit>** . A caixa de diálogo **Editar Plataformas de Solução** é aberta.

3. Clique na plataforma que deseja remover e clique em **Remover**.

## <a name="targeting-multiple-platforms-with-one-solution"></a>Destinando-se a várias plataformas com uma solução
 Uma vez que pode alterar as configurações com base na combinação de definições de plataforma e de configuração, você pode configurar uma solução que pode ter mais de uma plataforma de destino.

#### <a name="to-target-multiple-platforms"></a>Para destinar-se a várias plataformas

1. Use o **Configuration Manager** para adicionar pelo menos duas plataformas de destino para a solução.

2. Selecione a plataforma a que deseja se destinar na lista **Plataforma da solução ativa**.

3. Compile a solução.

#### <a name="to-build-multiple-solution-configurations-at-once"></a>Para criar várias configurações de solução de uma vez

1. Use o **Configuration Manager** para adicionar pelo menos duas plataformas de destino para a solução.

2. Use a janela **Build em Lotes** para criar várias configurações de solução de uma vez.

   É possível ter uma plataforma de solução definida como, por exemplo, [!INCLUDE[vcprx64](../includes/vcprx64-md.md)], e não ter projetos na solução destinados à mesma plataforma. Também é possível ter vários projetos em sua solução, cada um destinado a plataformas diferentes. É recomendável que, se tiver uma dessas situações, você crie uma nova configuração com um nome descritivo para evitar confusão.

## <a name="see-also"></a>Consulte Também
 [Como: criar e editar configurações que](../ide/how-to-create-and-edit-configurations.md) [compreendem as configurações de compilação](../ide/understanding-build-configurations.md) [criando e limpando projetos e soluções no Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
