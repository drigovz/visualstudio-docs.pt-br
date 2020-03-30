---
title: Implantar aplicativos ClickOnce sem reassinar
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89e1d7970b26d5ba9bd49090362a6a4e8c09f78d
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395319"
---
# <a name="deploy-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Implantar aplicativos ClickOnce para testes e servidores de produção sem demissão
Este artigo descreve um recurso do ClickOnce introduzido na versão 3.5 do .NET Framework que permite a implantação de aplicativos ClickOnce a partir de vários locais de rede sem reassinar ou alterar os manifestos do ClickOnce.

> [!NOTE]
> A demissão ainda é o método preferido para implantar novas versões de aplicativos. Sempre que possível, use o método de demissão. Para obter mais informações, consulte [ *Mage.exe* (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

 Desenvolvedores de terceiros e ISVs podem optar por esse recurso, facilitando a atualização de seus aplicativos por seus clientes. Este recurso pode ser usado nas seguintes situações:

- Ao atualizar um aplicativo, não para a primeira instalação de um aplicativo.

- Quando há apenas uma configuração do aplicativo em um computador. Por exemplo, se um aplicativo estiver configurado para apontar para dois bancos de dados diferentes, você não poderá usar esse recurso.

## <a name="exclude-deploymentprovider-from-deployment-manifests"></a>Excluir implantaçãoProvedor de manifestos de implantação
 No .NET Framework 2.0 e no .NET Framework 3.0, qualquer aplicativo ClickOnce que `deploymentProvider` instale no sistema para disponibilidade offline deve listar um em seu manifesto de implantação. O `deploymentProvider` é frequentemente referido como o local de atualização; é o local onde o ClickOnce verifica as atualizações do aplicativo. Esse requisito, juntamente com a necessidade de os editores de aplicativos assinarem suas implantações, tornou difícil para uma empresa atualizar um aplicativo ClickOnce de um fornecedor ou outro terceiro. Também torna mais difícil implantar o mesmo aplicativo de vários locais na mesma rede.

 Com as alterações feitas para o ClickOnce no Quadro .NET 3.5, é possível que um terceiro forneça um aplicativo ClickOnce para outra organização, que pode então implantar o aplicativo em sua própria rede.

 Para aproveitar esse recurso, os desenvolvedores dos aplicativos `deploymentProvider` ClickOnce devem excluir de seus manifestos de implantação. Este requisito significa que `-providerUrl` você deve excluir o argumento quando criar manifestos de implantação com o Mage.exe. Ou, se você estiver gerando manifestos de implantação com MageUI.exe, você deve certificar-se de que a caixa de texto **Local de lançamento** na guia Manifesto do **aplicativo** seja deixada em branco.

## <a name="deploymentprovider-and-application-updates"></a>implantaçãoAtualizações de provedores e aplicativos
 Começando com o .NET Framework 3.5, você `deploymentProvider` não precisa mais especificar um manifesto de implantação para implantar um aplicativo ClickOnce para uso on-line e off-line. Essa mudança suporta o cenário em que você precisa empacotar e assinar a implantação você mesmo, mas permitir que outras empresas implantem o aplicativo em suas redes.

 O ponto importante a ser lembrado `deploymentProvider` é que os aplicativos que excluem um não podem `deploymentProvider` alterar sua localização de instalação durante as atualizações, até que eles enviam uma atualização que inclua a tag novamente.

 Aqui estão dois exemplos para esclarecer este ponto. No primeiro exemplo, você publica um `deploymentProvider` aplicativo ClickOnce que não tem `http://www.adatum.com/MyApplication/`tag e pede aos usuários para instalá-lo a partir de . Se você decidir publicar a próxima atualização `http://subdomain.adatum.com/MyApplication/`do aplicativo de , você não tem como significar `http://www.adatum.com/MyApplication/`isso no manifesto de implantação que reside em . Você pode fazer uma de duas coisas:

- Diga aos seus usuários para desinstalar a versão anterior e instalar a nova versão a partir do novo local.

- Inclua uma `http://www.adatum.com/MyApplication/` atualização que `deploymentProvider` inclua `http://www.adatum.com/MyApplication/`um apontamento para . Em seguida, libere `deploymentProvider` outra `http://subdomain.adatum.com/MyApplication/`atualização mais tarde apontando para .

  No segundo exemplo, você publica um `deploymentProvider`aplicativo ClickOnce que especifica e, em seguida, decide removê-lo. Uma vez que `deploymentProvider` a nova versão sem é baixada para os clientes, você não `deploymentProvider` pode redirecionar o caminho usado para atualizações até que você libere uma versão do seu aplicativo que foi restaurada. Como no primeiro `deploymentProvider` exemplo, deve inicialmente apontar para o local de atualização atual, não para sua nova localização. Neste caso, se você tentar `deploymentProvider` inserir um `http://subdomain.adatum.com/MyApplication/`que se refere a , então a próxima atualização falhará.

## <a name="create-a-deployment"></a>Criar uma implantação
 Para obter orientações passo a passo sobre a criação de implantações que podem ser implantadas em diferentes locais de rede, consulte [Passo a Passo: Implante manualmente um aplicativo ClickOnce que não requer re-assinatura e que preserva as informações de marca](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md).

## <a name="see-also"></a>Confira também
- [*Mage.exe* (Ferramenta de Geração e Edição de Manifesto)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [*MageUI.exe* (Ferramenta de Geração e Edição de Manifesto, Cliente Gráfico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
