---
title: Solução de problemas de empacotamento e implantação do SharePoint | Microsoft Docs
description: Entenda e corrija vários problemas que você pode encontrar ao empacotar e implantar soluções do SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/22/2017
ms.topic: conceptual
f1_keywords:
- VSTO.WorkflowDeployment.Troubleshooting
- VS.SharePointTools.Project.PackageRetraction
- VS.SharePointTools.Deployment.Troubleshooting
- VS.SharePointTools.Deploying.Troubleshooting
- VS.SharePointTools.Project.DeploymentTroubleshooting
- VS.SharePointTools.Project.SharePointNotInstalled
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
- SharePoint development in Visual Studio, troubleshooting
- SharePoint development in Visual Studio, deployment conflict resolution
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f3ef56ba868700699eaaeb8ec88291fd6f8d8d32
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892301"
---
# <a name="troubleshoot-sharepoint-packaging-and-deployment"></a>Solução de problemas de empacotamento e implantação do SharePoint
  Este tópico aborda vários problemas que você pode encontrar ao empacotar e implantar soluções do SharePoint.

## <a name="enable-enhanced-debugging"></a>Habilitar depuração avançada
 Para diagnosticar entre o Visual Studio, o SharePoint e outras camadas, você pode usar a chave do registro EnableDiagnostics para exibir o rastreamento de pilha. Para obter mais informações, consulte [depurar soluções do SharePoint](../sharepoint/debugging-sharepoint-solutions.md).

## <a name="add-project-output-to-the-solution-package"></a>Adicionar saída do projeto ao pacote de solução
 Você pode adicionar a saída do projeto a um pacote por meio do designer de pacotes. No entanto, ao adicionar a saída do projeto, verifique se a plataforma do projeto corresponde à plataforma da solução do SharePoint. Recomendamos que você use qualquer destino de plataforma de **CPU** para os assemblies que você deseja implantar em um servidor do SharePoint. Para obter mais informações, consulte [Compilar página, designer de projeto &#40;Visual Basic&#41;](../ide/reference/compile-page-project-designer-visual-basic.md) e [caixa de diálogo Configurações avançadas do compilador &#40;Visual Basic ](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)&#41;.

## <a name="validation-warnings-and-errors"></a>Avisos e erros de validação
 As ferramentas de desenvolvimento do SharePoint no Visual Studio executam etapas de validação para verificar se o pacote de solução está formado corretamente. Você também pode criar etapas de validação personalizadas para seus recursos e pacotes. Para obter mais informações, consulte [como criar regras personalizadas de validação de pacotes e recursos para soluções do SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

## <a name="deployment-conflict-resolution"></a>Resolução de conflito de implantação
 Ao implantar uma solução do SharePoint, você poderá encontrar colisões quando um item no servidor tiver o mesmo nome, URL ou ID de um item em seu pacote de solução. Você pode alterar a propriedade de **resolução de conflito de implantação** para resolver, relatar ou ignorar colisões de módulos, Web Parts, instâncias de lista e tipos de conteúdo.

 A tabela a seguir demonstra as configurações para a propriedade de **resolução de conflito de implantação** .

|Valor|Descrição|
|-----------|-----------------|
|Automático|Detecta colisões e resolve os conflitos automaticamente.|
|Prompt|Detecta colisões e as relata para o desenvolvedor antes de resolver os conflitos.|
|Nenhum|Não detecta colisões.|

## <a name="differences-between-f5-deployment"></a>Diferenças entre a implantação F5
 Quando você usa [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] o para implantar seu projeto do SharePoint no servidor do SharePoint local para teste e depuração, há algumas etapas adicionais que são executadas pelo [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

1. Redefina o IIS (serviço de informações da Internet) durante a etapa de implantação.

2. Associar fluxos de trabalho automaticamente.

3. Defina a ordem de ativação do recurso de acordo com a hierarquia no designer de pacotes.

   Você pode adicionar etapas de implantação personalizadas para alterar ainda mais o comportamento de **F5** . Para obter mais informações, consulte [Walkthrough: criar uma etapa de implantação personalizada para projetos do SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="delay-displaying-sharepoint-page-when-deploy-visual-web-part"></a>Atrasar a exibição da página do SharePoint ao implantar Web Part Visual
 A página do SharePoint leva muito tempo para aparecer ao implantar uma Web Part Visual na pasta bin em [!INCLUDE[wiprlhext](../sharepoint/includes/wiprlhext-md.md)] , [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] ou [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] . Se você alterar todos os arquivos em um diretório de nível superior [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] , como o diretório bin, todo o aplicativo Web será recompilado. Isso pode causar um atraso de até 25 segundos para que a página do SharePoint seja renderizada.

### <a name="error-message"></a>Mensagem de erro
 Nenhum.

### <a name="resolution"></a>Resolução
 Para contornar esse problema, execute as seguintes etapas:

1. Instale a atualização KB967535 conforme descrito no artigo de Suporte da Microsoft [correção: um hotfix está disponível para corrigir dois problemas no ASP.net no IIS 7,0 para Windows Vista e Windows Server 2008](https://support.microsoft.com/help/967535).

2. Adicione a seguinte linha ao arquivo de Web.config:

    ```xml
    <compilation batch="false" optimizeCompilations="true">
    ```

## <a name="sharepoint-project-deployment-fails-with-error-failed-to-extract-the-cab-file-in-the-solution"></a>A implantação do projeto do SharePoint falha com o erro "falha ao extrair o arquivo CAB na solução"
 Se o nome de qualquer item de projeto do SharePoint contiver parênteses, sua solução falhará na implantação com um erro.

### <a name="error-message"></a>Mensagem de erro
 Ocorreu um erro na etapa de implantação ' Adicionar solução ': falha ao extrair o arquivo CAB na solução.

### <a name="resolution"></a>Resolução
 Para contornar esse problema, remova os parênteses nos nomes dos itens de projeto do SharePoint.

## <a name="error-appears-when-deploying-a-visual-web-part-to-a-site-on-a-different-web-application"></a>O erro é exibido ao implantar uma Web Part Visual em um site em um aplicativo Web diferente
 Na primeira vez que você implantar uma Web Part Visual em um site em um aplicativo Web diferente daquele no qual ele está atualmente implantado (alterando a propriedade SiteUrl do Visual Web Part), você receberá um erro.

### <a name="error-message"></a>Mensagem de erro
 Ocorreu um erro na etapa de implantação ' Adicionar solução ': um recurso com a ID [#] já foi instalado neste farm. Use o atributo Force para reinstalar explicitamente o recurso.

### <a name="resolution"></a>Resolução
 Esse erro ocorre devido à maneira como os recursos visuais da Web Part são retraídos no SharePoint. Para implantar com êxito a Web Part Visual, implante a solução novamente escolhendo a tecla **F5** .

## <a name="warning-appears-when-deploying-nested-user-controls"></a>O aviso aparece ao implantar controles de usuário aninhados
 Esse aviso ocorre quando você implanta uma solução do SharePoint que tem controles de usuário aninhados, como uma Web Part Visual que contém um controle de usuário ou um controle de usuário que contém uma Web Part Visual ou outro controle de usuário. Esse aviso ocorrerá se você adicionar um controle a um designer arrastando-o da caixa de ferramentas ou usando a @Register diretiva na exibição de origem.

### <a name="error-message"></a>Mensagem de erro
 O elemento de aviso 1 ' [*nome do controle*] ' não é um elemento conhecido. Isso pode ocorrer se houver um erro de compilação no site ou se o arquivo web.config estiver ausente.

### <a name="resolution"></a>Resolução
 Se o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sistema do projeto não estiver ciente de um controle de usuário aninhado, ele não poderá fornecer o IntelliSense e emitirá o aviso. O sistema do projeto não saberá de um controle de usuário aninhado se o projeto não for compilado e o designer não for fechado e reaberto, ou se a opção de cancelamento automático estiver habilitada, o que faz com que o controle de usuário seja retraído do hive do SharePoint após a depuração.

 Para remover esse aviso, compile o projeto e, em seguida, feche e reabra o designer ou desabilite a opção de cancelamento automático para o projeto. Para fazer isso, desmarque a caixa de seleção **Cancelar automaticamente após a depuração** na guia **SharePoint** da caixa de diálogo Propriedades do projeto.

## <a name="see-also"></a>Confira também

- [Empacotar e implantar soluções do SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)