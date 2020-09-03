---
title: Implantando aplicativos ClickOnce para servidores de teste e produção sem assinatura | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, deploying without resigning
- ClickOnce deployment, without resigning
- application updates, ClickOnce
- update location [ClickOnce]
- deploymentProvider tag
- manifests [ClickOnce]
ms.assetid: 1218a98d-1ad5-4eef-95dd-0e0b3c44168c
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a8e41e67d5e2800acc41e1220fe632001420a274
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80395380"
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Implantando aplicativos ClickOnce para servidores de teste e produção sem assinar novamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tópico aborda um novo recurso do ClickOnce introduzido na versão .NET Framework 3,5 que permite a implantação de aplicativos ClickOnce de vários locais de rede sem assinar novamente ou alterar os manifestos ClickOnce.  
  
> [!NOTE]
> A reassinatura ainda é o método preferencial para implantar novas versões de aplicativos. Sempre que possível, use o método de assinatura. Para obter mais informações, consulte [Mage.exe (manifest Generation and Editing Tool)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
 Desenvolvedores e ISVs de terceiros podem optar por aceitar esse recurso, facilitando a atualização de seus aplicativos pelos clientes. Esse recurso pode ser usado nas seguintes situações:  
  
- Ao atualizar um aplicativo, não a primeira instalação de um aplicativo.  
  
- Quando há apenas uma configuração do aplicativo em um computador. Por exemplo, se um aplicativo estiver configurado para apontar para dois bancos de dados diferentes, você não poderá usar esse recurso.  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>Excluindo deploymentProvider de manifestos de implantação  
 No .NET Framework 2,0 e no .NET Framework 3,0, qualquer aplicativo ClickOnce instalado no sistema para disponibilidade offline deve especificar um `deploymentProvider` em seu manifesto de implantação. O `deploymentProvider` é geralmente referido como o local de atualização; é o local em que o ClickOnce verificará se há atualizações do aplicativo. Esse requisito, juntamente com a necessidade de que os editores de aplicativos assinem suas implantações, dificultava para uma empresa atualizar um aplicativo ClickOnce de um fornecedor ou de terceiros. Isso também dificulta a implantação do mesmo aplicativo de vários locais na mesma rede.  
  
 Com as alterações feitas no ClickOnce no .NET Framework 3,5, é possível que um terceiro forneça um aplicativo ClickOnce para outra organização, que pode então implantar o aplicativo em sua própria rede.  
  
 Para aproveitar esse recurso, os desenvolvedores de aplicativos ClickOnce devem excluir `deploymentProvider` de seus manifestos de implantação. Isso significa excluir o `-providerUrl` argumento ao criar manifestos de implantação com Mage.exe, ou certificar-se de que a caixa de texto **local de inicialização** na guia **manifesto do aplicativo** será deixada em branco se você estiver gerando manifestos de implantação com MageUI.exe.  
  
## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider e atualizações de aplicativo  
 A partir do .NET Framework 3,5, você não precisa mais especificar um `deploymentProvider` em seu manifesto de implantação para implantar um aplicativo ClickOnce para uso online e offline. Isso dá suporte ao cenário em que você precisa empacotar e assinar a implantação por conta própria, mas permitir que outras empresas implantem o aplicativo em suas redes.  
  
 O ponto principal a ser lembrado é que os aplicativos que excluem um `deploymentProvider` não podem alterar o local de instalação durante as atualizações, até que eles enviem uma atualização que inclua a `deploymentProvider` marca novamente.  
  
 Aqui estão dois exemplos para esclarecer esse ponto. No primeiro exemplo, você publica um aplicativo ClickOnce que não tem nenhuma `deploymentProvider` marca e solicita que os usuários o instalem do `http://www.adatum.com/MyApplication/` . Se você decidir que deseja publicar a próxima atualização do aplicativo do `http://subdomain.adatum.com/MyApplication/` , não terá nenhuma maneira de significar isso no manifesto de implantação que reside no `http://www.adatum.com/MyApplication/` . Você pode fazer uma das duas coisas:  
  
- Diga aos usuários para desinstalar a versão anterior e instalar a nova versão do novo local.  
  
- Inclua uma atualização no `http://www.adatum.com/MyApplication/` que inclua um `deploymentProvider` apontando para `http://www.adatum.com/MyApplication/` . Em seguida, libere outra atualização posteriormente `deploymentProvider` apontando para `http://subdomain.adatum.com/MyApplication/` .  
  
  No segundo exemplo, você publica um aplicativo ClickOnce que especifica `deploymentProvider` e, em seguida, decide removê-lo. Depois que a nova versão sem `deploymentProvider` tiver sido baixada para os clientes, você não poderá redirecionar o caminho usado para atualizações até liberar uma versão do aplicativo que foi `deploymentProvider` restaurada. Como no primeiro exemplo, `deploymentProvider` deve apontar inicialmente para o local de atualização atual, não para o seu novo local. Nesse caso, se você tentar inserir um `deploymentProvider` que se refere a `http://subdomain.adatum.com/MyApplication/` , a próxima atualização falhará.  
  
## <a name="creating-a-deployment"></a>Criando uma implantação  
 Para obter orientação passo a passo sobre como criar implantações que podem ser implantadas de diferentes locais de rede, consulte [passo a passos: Implantando manualmente um aplicativo ClickOnce que não requer nova assinatura e que preserva informações de identidade visual](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required?view=vs-2015).  
  
## <a name="see-also"></a>Consulte Também  
 [Mage.exe (Manifest Generation and Editing Tool)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (Manifest Generation and Editing Tool, cliente gráfico)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)
