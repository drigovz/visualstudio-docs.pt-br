---
title: Acessando Máquinas Virtuais do Azure do Gerenciador de Servidores | Microsoft Docs
description: Obtenha uma visão geral de como exibir e gerenciar máquinas virtuais (VMs) do Azure no Gerenciador de Servidores no Visual Studio.
author: ghogen
manager: jillfra
assetId: eb3afde6-ba90-4308-9ac1-3cc29da4ede0
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/31/2017
ms.author: ghogen
ms.openlocfilehash: 12f94605ee6a1f4e4cc0142e6dd59ec02ed619c9
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849949"
---
# <a name="accessing-azure-virtual-machines-from-server-explorer"></a>Acessando máquinas virtuais do Azure no Gerenciador de Servidores

Se você tiver máquinas virtuais hospedadas pelo Azure, poderá acessá-las no Gerenciador de Servidores. Você primeiro deve entrar sua assinatura do Azure para exibir os serviços móveis. Por exemplo, no Gerenciador de Servidores, você pode abrir o menu de atalho do nó do Azure e escolher **Conectar ao Microsoft Azure**.

1. No Cloud Explorer, escolha uma máquina virtual e pressione a tecla F4 para mostrar a respectiva janela de propriedades.

    A tabela a seguir mostra quais propriedades estão disponíveis, mas elas são somente leitura. Para alterá-las, use o [Portal do Azure](https://portal.azure.com/).

   | propriedade | Descrição |
   | --- | --- |
   | Nome DNS |A URL com o endereço de Internet da máquina virtual. |
   | Ambiente |Para uma máquina virtual, o valor dessa propriedade é sempre produção. |
   | Name |O nome da máquina virtual. |
   | Tamanho |O tamanho da máquina virtual, que reflete a quantidade de memória e espaço em disco disponível. Para obter mais informações, consulte os [tamanhos de máquina virtual](https://docs.microsoft.com/azure/cloud-services/cloud-services-sizes-specs). |
   | Status |Os valores incluem Inicial, Iniciado, Parando, Parado e Recuperando Status. Se Recuperando Status aparecer, o status atual é desconhecido. Os valores para essa propriedade diferem dos valores que são usados no [Portal do Azure](https://portal.azure.com/). |
   | SubscriptionID |A ID de assinatura para sua conta do Azure. Você pode mostrar essas informações no [Portal do Azure](https://portal.azure.com/) exibindo as propriedades de uma assinatura. |
2. Escolha um nó do ponto de extremidade e exiba a janela **Propriedades** .
3. A tabela a seguir descreve as propriedades de pontos de extremidade disponíveis, mas eles são somente leitura. Para adicionar ou editar os pontos de extremidade para uma máquina virtual, use o [Portal do Azure](https://portal.azure.com/). 

   | propriedade | Descrição |
   | --- | --- |
   | Name |Um identificador para o ponto de extremidade. |
   | Porta privada |A porta para acesso à rede interna para o seu aplicativo. |
   | Protocolo |O protocolo de camada de transporte que este ponto de extremidade usa: TCP ou UDP. |
   | Porta pública |A porta usada para acesso público ao seu aplicativo. |
