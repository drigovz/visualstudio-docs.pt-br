---
title: Projetar e criar soluções do Office
description: Saiba como o Visual Studio fornece modelos de projeto que você pode usar para criar vários tipos diferentes de soluções do Office.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], creating
- Office development in Visual Studio, creating solutions
- solutions [Office development in Visual Studio], creating
- Office project types in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: df634a7c242819e4f41a6fddeae4099a3d25fae2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897634"
---
# <a name="design-and-create-office-solutions"></a>Projetar e criar soluções do Office

O Visual Studio fornece modelos de projeto que você pode usar para criar vários tipos diferentes de soluções do Office. Esta seção da documentação descreve os modelos de projeto e fornece orientação sobre como criar projetos do Office. Para obter informações sobre como implementar personalizações de código e de interface do usuário depois de criar seu projeto, consulte [desenvolver soluções do Office](../vsto/developing-office-solutions.md).

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="create-office-projects"></a>Criar projetos do Office
 Antes de começar, você deve determinar seus requisitos e descobrir o tipo de solução que oferece o melhor ajuste. Por exemplo, se a solução do Office precisar ser executada toda vez que o aplicativo for usado, um suplemento do VSTO atenderá melhor às suas necessidades. Se o código estiver totalmente integrado a um único documento, crie uma personalização no nível do documento. Esses tipos de projeto estão disponíveis como modelos de projeto do Visual Studio. Para obter mais informações sobre os modelos de projeto do Office incluídos no Visual Studio, consulte [visão geral dos modelos de projeto do Office](../vsto/office-project-templates-overview.md). Para obter mais informações sobre como criar projetos do Office, consulte [como criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Os projetos do Office têm recursos e itens de projeto que são diferentes de outros tipos de projetos no Visual Studio. Por exemplo, quando você cria um projeto de nível de documento, o documento ou pasta de trabalho em seu projeto pode ser aberto e editado dentro do Visual Studio. Para obter mais informações, consulte [projetos do Office no ambiente do Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="choose-a-net-framework-version"></a>Escolher uma versão .NET Framework
 Depois de selecionar o tipo de projeto que melhor atenda às suas necessidades, você pode escolher qual versão do .NET Framework usar em seu processo de desenvolvimento. Você pode direcionar as seguintes versões de .NET Framework em projetos do Office:

- [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]

- [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]

- [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]

  A versão de .NET Framework que você escolhe para seu projeto é necessária nos computadores dos usuários finais para que sua solução seja executada. Por exemplo, se o seu projeto for direcionado para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] será necessário nos computadores dos usuários finais. Neste exemplo, sua solução não será executada se apenas o .NET Framework 3,5 estiver instalado nos computadores dos usuários finais.

  Se você migrar um projeto de suplemento do VSTO destinado ao .NET Framework 3,5, o Visual Studio alterará a estrutura de destino do seu projeto para [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, dependendo da versão do Office instalada.

  No entanto, depois que o Visual Studio alterar a estrutura de destino, talvez seja necessário modificar parte do código em seu projeto se ele usar determinados recursos. Para obter mais informações sobre como alterar a estrutura de destino, consulte [como: direcionar uma versão do .NET Framework](../ide/visual-studio-multi-targeting-overview.md). Para obter mais informações sobre as alterações que talvez você precise fazer em seu projeto, consulte [migrar soluções do Office para o .NET Framework 4 ou posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).

  Se o Visual Studio alterar o .NET Framework de destino para seu projeto e você estiver usando o ClickOnce para implantar sua solução, certifique-se de selecionar também a versão correspondente do .NET Framework na caixa de diálogo **pré-requisitos** . Essa seleção não é alterada automaticamente quando você altera a estrutura de destino do seu projeto. Para obter mais informações, consulte [como: instalar pré-requisitos em computadores de usuários finais para executar soluções do Office](/previous-versions/bb608608(v=vs.110)).

> [!NOTE]
> Não é possível direcionar o .NET Framework 3,5 ou anterior em projetos do Office que você cria usando o [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] . Os projetos do Office que você cria usando [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] exigem recursos que foram introduzidos pela primeira vez no [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]

### <a name="understand-when-the-office-pias-are-required-on-end-user-computers"></a>Entenda quando os PIAs do Office são necessários nos computadores dos usuários finais
 Por padrão, os assemblies de interoperabilidade primária do Office (PIAs) não precisam ser instalados nos computadores dos usuários finais se a propriedade **inserir tipos de interoperabilidade** de cada referência do pia do Office no projeto estiver definida como **true**, que é o valor padrão. Nesse cenário, as informações de tipo para os tipos de PIA usados pela sua solução são inseridas no assembly da solução quando você cria o projeto. Em tempo de execução, as informações de tipo inserido são usadas em vez dos PIAs para chamar o modelo de objeto baseado em COM do aplicativo do Office. Para obter mais informações sobre como os tipos de PIAs são inseridos em sua solução, consulte [equivalência e tipos de interoperabilidade inseridos](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types).

 Se a propriedade **inserir tipos de interoperabilidade** de cada referência do pia do Office no projeto estiver definida como **false**, os pias do Office deverão ser instalados e registrados no cache de assembly global em cada computador do usuário final que executa a solução. Na maioria dos casos, os PIAs são instalados por padrão com o Office, mas você também pode incluir o PIA redistribuível como um pré-requisito para sua solução. Para obter mais informações, consulte [pré-requisitos da solução do Office para implantação](/previous-versions/bb608617(v=vs.110)).

### <a name="understand-the-client-profile"></a>Entender o perfil do cliente
 O perfil de cliente do .NET Framework é um subconjunto do .NET Framework completo. Você pode direcionar o perfil de cliente do .NET Framework se precisar usar apenas os recursos do cliente no .NET Framework e desejar fornecer a experiência de implantação mais rápida possível para sua solução do Office. Para obter mais informações, consulte [.NET Framework perfil do cliente](/dotnet/framework/deployment/client-profile).

 Quando você cria um projeto do Office direcionado [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] para o, o [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] é direcionado por padrão. Se você quiser desenvolver para o completo [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , deverá definir essa opção depois que o projeto for criado. Para obter mais informações, consulte [Como direcionar a uma versão do .NET Framework](../ide/visual-studio-multi-targeting-overview.md).

## <a name="create-solutions-for-the-64-bit-edition-of-microsoft-office"></a>Criar soluções para a edição de 64 bits do Microsoft Office
 Microsoft Office está disponível em edições de 64 bits e 32 bits. Para criar soluções do Office que podem ser executadas em qualquer edição, a configuração de plataforma de destino para seu projeto deve ser definida como **qualquer CPU**. Esse é o valor padrão para projetos do Office. Para obter mais informações, consulte [criar soluções do Office](../vsto/building-office-solutions.md).

 Há versões separadas de 64 bits e 32 bits do [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] que são usadas pelas edições de 64 bits e de 32 bits do Microsoft Office. Para obter mais informações, consulte [visão geral do ferramentas do Visual Studio para Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="assemblies-in-office-solutions"></a>Assemblies em soluções do Office
 Quando você cria um projeto do Office usando as ferramentas de desenvolvimento do Office no Visual Studio, o código que você escreve é eventualmente compilado em um assembly. O assembly é implantado em um servidor compartilhado ou em um diretório no computador cliente.

 Os assemblies nas soluções do Office são carregados por um aplicativo do Office. Depois que o assembly é carregado, o código no assembly pode responder a eventos que são gerados no aplicativo, por exemplo, quando um usuário clica em um item de menu. O código no assembly também pode chamar o modelo de objeto para automatizar e estender o aplicativo e pode usar qualquer uma das classes no [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] . Para obter mais informações, consulte [arquitetura de personalizações em nível de documento](../vsto/architecture-of-document-level-customizations.md) e [arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md).

 As soluções do Office usam manifestos de implantação e manifestos de aplicativo para identificar o assembly. Os manifestos contêm informações sobre o nome, a versão e o local do assembly, para que o aplicativo possa localizar, vincular e executar o assembly correto. Para obter mais informações, consulte [manifestos de aplicativo e implantação em soluções do Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).

 Projetos de nível de documento incluem um documento além de um assembly. O documento atua como o front-end do aplicativo e é onde toda a interação do usuário ocorre. Cada documento pode ter apenas um assembly de projeto principal associado a ele; no entanto, vários documentos podem apontar para o mesmo assembly.

 Os assemblies em projetos de nível de documento não são inseridos no documento; em vez disso, eles são armazenados em outro lugar e são identificados pelo manifesto do aplicativo do documento.

## <a name="security-considerations-for-assemblies"></a>Considerações de segurança para assemblies
 Para que uma solução do Office seja executada em um computador, os assemblies usados pela solução devem ser confiáveis para execução. Para obter mais informações sobre segurança, consulte [proteger soluções do Office](../vsto/securing-office-solutions.md).

 Por padrão, o assembly da solução e todos os assemblies referenciados que estão na pasta de saída do projeto são confiáveis para serem executados no computador de desenvolvimento quando você cria o projeto. Para obter mais informações, consulte [criar soluções do Office](../vsto/building-office-solutions.md).

 Por motivos de segurança, é melhor criar projetos em seu computador local, em vez de desenvolver em um local compartilhado. Para obter mais informações, consulte [desenvolvimento colaborativo de soluções do Office](../vsto/collaborative-development-of-office-solutions.md).

## <a name="referenced-assemblies"></a>Assemblies referenciados
 O assembly pode fazer referência a outros assemblies, que são listados nas referências do projeto. No entanto, um assembly de projeto em nível de documento não pode fazer referência a outro assembly de projeto de nível de documento.

## <a name="see-also"></a>Confira também
- [Visão geral dos modelos do Office Project](../vsto/office-project-templates-overview.md)
- [Como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Projetos do Office no ambiente do Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md)
- [Propriedades em projetos do Office](../vsto/properties-in-office-projects.md)
- [Executar soluções em versões diferentes do Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)
- [Como: direcionar aplicativos do Office por meio de assemblies de interoperabilidade primária](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Manifestos de aplicativo e implantação em soluções do Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [Como definir informações de configuração para uma solução do Office](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md)
- [Usar a funcionalidade do Office dentro do Visual Studio](../vsto/using-office-functionality-inside-of-visual-studio.md)
- [Implantar uma solução do Office](../vsto/deploying-an-office-solution.md)
- [Tarefas comuns na programação do Office](../vsto/common-tasks-in-office-programming.md)
- [Desenvolver soluções do Office](../vsto/developing-office-solutions.md)
- [Arquitetura de soluções do Office no Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)