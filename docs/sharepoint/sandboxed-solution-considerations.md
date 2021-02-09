---
title: Considerações sobre a solução em área restrita | Microsoft Docs
description: Explore soluções em área restrita, que são um recurso do Microsoft SharePoint que permite que os usuários do conjunto de sites Carreguem suas próprias soluções de código personalizado.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SandboxedSolutions
- VS.SharePointTools.Security.SandboxedSolutions
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 23424c1681a9967d9d50df47f9e67ec895a308a1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881601"
---
# <a name="sandboxed-solution-considerations"></a>Considerações sobre a solução em área restrita
  As *soluções de área restrita* são um recurso do Microsoft SharePoint 2010 que permite que os usuários do conjunto de sites Carreguem suas próprias soluções de código personalizado. Uma solução em área restrita comum é que os usuários carregam seus próprios Web Parts.

 Um aplicativo do SharePoint em área restrita é executado em um processo seguro e monitorado que tem acesso a uma parte limitada do Web farm. O Microsoft SharePoint 2010 usa uma combinação de recursos, galerias de soluções, monitoramento de soluções e uma estrutura de validação para habilitar soluções em área restrita.

## <a name="specify-project-trust-level"></a>Especificar nível de confiança do projeto
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dá suporte a soluções em área restrita por meio de uma propriedade de projeto booliana chamada *solução de área restrita*. Essa propriedade pode ser definida a qualquer momento no projeto ou pode ser especificada quando você cria o projeto no **Assistente para personalização do SharePoint**.

> [!NOTE]
> Alterar a propriedade da *solução de área restrita* de um projeto após sua criação pode causar erros de validação.

 A solução será considerada uma solução no escopo do farm se a propriedade da *solução de área restrita* estiver definida como **false** ou se você escolher a opção **implantar como uma solução de farm** . No entanto, a solução será tratada de forma diferente de uma solução de farm se a propriedade de *solução de área restrita* estiver definida como **true** ou se você escolher a opção **implantar como uma solução de área restrita** no assistente.

## <a name="sharepoint-site-hierarchy"></a>Hierarquia de site do SharePoint
 Para entender como funcionam as soluções em área restrita, é útil saber que os sites do SharePoint são hierárquicos no escopo. O elemento superior é conhecido como Web farm e outros elementos são subordinados a ele:

 Web Farm

 Aplicativo Web A

 Conjunto de sites a1

 A1A do site

 Aplicativo Web B

 Conjunto de sites B1

 B1a do site

 B1b do site

 Conjunto de sites B2

 B2a do site

 Como você pode ver, os Web farms podem conter um ou mais aplicativos Web que, por sua vez, podem conter um ou mais conjuntos de sites, que podem ter subsites e assim por diante. As alterações feitas em um conjunto de sites afetam apenas esse conjunto de sites e nenhum outro. No entanto, as alterações feitas no nível do farm da Web afetam todos os conjuntos de sites no farm.

 O Windows SharePoint Services (WSS) 3,0 permite que você implante soluções somente no nível do farm, mas [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] permite que você implante no nível do farm (solução de farm) ou no nível de conjunto de sites (solução de área restrita).

## <a name="why-sandboxed-solutions"></a>Por que soluções em área restrita?
 No WSS 3,0, as soluções podiam ser implantadas somente no nível do farm. Isso significava que soluções potencialmente perigosas ou de desestabilização poderiam ser implantadas que afetaram todo o Web farm e todos os outros conjuntos de sites e aplicativos que são executados sob ele. No entanto, usando soluções de área restrita, você pode implantar suas soluções em uma subárea do farm, um conjunto de sites específico. Para fornecer proteção adicional, o assembly da solução não é carregado no processo principal [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] (*w3wp.exe*). Em vez disso, ele é carregado em um processo separado (*SPUCWorkerProcess.exe*). Esse processo é monitorado e implementa cotas e limitação para proteger o farm de soluções em área restrita que executam atividades prejudiciais, como a execução de loops apertados que consomem ciclos de CPU.

## <a name="site-collection-solution-gallery"></a>Galeria de soluções do conjunto de sites
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 2010 tem um recurso conhecido como "Galeria de soluções de conjunto de sites". Você pode acessar esse recurso na página Administração Central do SharePoint 2010 ou abrindo o menu **ações do site** , escolhendo **configurações do site** e escolhendo o link **soluções** em  **galerias** no site do SharePoint. Galerias de soluções são repositórios de soluções que permitem que os administradores de conjuntos de sites gerenciem soluções em seus conjuntos de sites.

 A Galeria de soluções é uma biblioteca de documentos armazenada na Web raiz do site do SharePoint. A Galeria de soluções substitui modelos de site e dá suporte a pacotes de solução. Quando um arquivo de pacote de solução do SharePoint (*. wsp*) é carregado, ele é processado como uma solução em área restrita.

## <a name="sandboxed-solution-limitations"></a>Limitações da solução em área restrita
 Quando uma solução em área restrita é implantada, a matriz de funcionalidade do SharePoint disponível para ela é limitada para ajudar a reduzir qualquer vulnerabilidade de segurança que ela possa ter. Algumas dessas limitações incluem o seguinte:

- As soluções de área restrita têm um subconjunto restrito de elementos de solução implantáveis disponíveis para eles. Os modelos de projeto do SharePoint potencialmente vulneráveis, como definições de site e fluxos de trabalho, não estão disponíveis.

- O SharePoint executa o código de solução em área restrita em um processo (*SPUCWorkerProcess.exe*) separado do [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] processo do pool de aplicativos principal (*w3wp.exe*).

- Pastas mapeadas não podem ser adicionadas ao projeto.

- Tipos no [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] assembly Microsoft. Office. Server não podem ser usados em soluções em área restrita. Além disso, somente os tipos no [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] assembly Microsoft. SharePoint podem ser usados em soluções em área restrita.

  É importante observar que a especificação de uma solução do SharePoint como uma solução de área restrita não tem nenhum efeito no SharePoint Server; Ele determina apenas como o projeto do SharePoint é implantado no SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e para quais assemblies ele se vincula. Ele não afeta o arquivo *. wsp* gerado e o arquivo *. wsp* não tem dados que correlacionem-se diretamente à propriedade de *solução de área restrita* .

## <a name="capabilities-and-elements-in-sandboxed-solutions"></a>Recursos e elementos em soluções de área restrita
 As soluções em área restrita dão suporte aos seguintes recursos e elementos:

- Tipos de conteúdo/campos

- Ações personalizadas

- Fluxos de trabalho declarativos

- Receptores de eventos

- Textos explicativos do recurso

- Listar definições

- Listar instâncias

- Módulo/arquivos

- Navegação

- *Onet.xml*

- SPItemEventReceiver

- SPListEventReceiver

- SPWebEventReceiver

- Suporte para todos os Web Parts que derivam de `System.Web.UI.WebControls.WebParts.WebPart`

- Partes de Web

- Elementos de recurso WebTemplate (em vez de *Webtemp.xml*)

- Web Parts Visual

  As soluções em área restrita não dão suporte aos seguintes recursos e elementos:

- Páginas do aplicativo

- Grupo de ação personalizado

- Recursos no escopo do farm

- Elemento `HideCustomAction`

- Recursos no escopo do aplicativo Web

- Fluxos de trabalho com código

## <a name="see-also"></a>Confira também
- [Diferenças entre soluções de área restrita e de farm](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)
- [Desenvolvendo soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)
