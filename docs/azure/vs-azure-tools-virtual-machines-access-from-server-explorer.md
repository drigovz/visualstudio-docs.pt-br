---
title: Acessando Máquinas Virtuais do Azure do Gerenciador de Servidores | Microsoft Docs
description: Obtenha uma visão geral de como exibir e gerenciar máquinas virtuais (VMs) do Azure no Gerenciador de Servidores no Visual Studio.
author: ghogen
manager: jmartens
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/31/2017
ms.author: ghogen
ms.openlocfilehash: a40434845187490ee4f8437f8e15963bddd1998f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99843781"
---
# <a name="accessing-azure-virtual-machines-from-server-explorer"></a>Acessando máquinas virtuais do Azure por meio do Gerenciador de Servidores

Se tiver máquinas virtuais hospedadas pelo Azure, você pode acessá-las no Gerenciador de Servidores. Você primeiro deve entrar sua assinatura do Azure para exibir os serviços móveis. Por exemplo, no Gerenciador de Servidores, você pode abrir o menu de atalho do nó do Azure e escolher **Conectar ao Microsoft Azure**.

1. No Cloud Explorer, escolha uma máquina virtual e pressione a tecla F4 para mostrar a respectiva janela de propriedades.

    A tabela a seguir mostra quais propriedades estão disponíveis, mas elas são somente leitura. Para alterá-las, use o [Portal do Azure](https://portal.azure.com).

   | Propriedade | Descrição |
   | --- | --- |
   | Nome DNS |A URL com o endereço de Internet da máquina virtual. |
   | Ambiente |Para uma máquina virtual, o valor dessa propriedade é sempre produção. |
   | Nome |O nome da máquina virtual. |
   | Tamanho |O tamanho da máquina virtual, que reflete a quantidade de memória e espaço em disco disponível. Para obter mais informações, consulte [tamanhos de máquina virtual](/azure/cloud-services/cloud-services-sizes-specs). |
   | Status |Os valores incluem Inicial, Iniciado, Parando, Parado e Recuperando Status. Se Recuperando Status aparecer, o status atual é desconhecido. Os valores para essa propriedade diferem dos valores que são usados no [Portal do Azure](https://portal.azure.com). |
   | SubscriptionID |A ID de assinatura para sua conta do Azure. Você pode mostrar essas informações no [Portal do Azure](https://portal.azure.com) exibindo as propriedades de uma assinatura. |
2. Escolha um nó do ponto de extremidade e exiba a janela **Propriedades**.
3. A tabela a seguir descreve as propriedades de pontos de extremidade disponíveis, mas eles são somente leitura. Para adicionar ou editar os pontos de extremidade para uma máquina virtual, use o [Portal do Azure](https://portal.azure.com).

   | Propriedade | Descrição |
   | --- | --- |
   | Nome |Um identificador para o ponto de extremidade. |
   | Porta privada |A porta para acesso à rede interna para o seu aplicativo. |
   | Protocolo |O protocolo de camada de transporte que este ponto de extremidade usa: TCP ou UDP. |
   | Porta pública |A porta usada para acesso público ao seu aplicativo. |
