---
title: Visão geral das propriedades do documento personalizado
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], custom properties
- custom document properties
- document-level customizations [Office development in Visual Studio], custom properties
- Office documents [Office development in Visual Studio], custom properties
- _AssemblyLocation property
- _AssemblyName property
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7b3f4038a05478d8e2d747efa700c7ece02e4827
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62951177"
---
# <a name="custom-document-properties-overview"></a>Visão geral das propriedades do documento personalizado

Quando você cria um projeto de nível de documento, o Visual Studio adiciona duas propriedades personalizadas ao documento no projeto: \_ AssemblyLocation e \_ AssemblyName. Quando um usuário abre um documento, o aplicativo Microsoft Office verifica essas propriedades de documento personalizadas. Se existirem no documento, o aplicativo carregará o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , o que iniciará a personalização. Para obter mais informações, consulte [arquitetura de soluções do Office no Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="_assemblyname"></a>\_AssemblyName

Essa propriedade contém o CLSID de uma interface no componente carregador de solução do Office do [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . O valor do CLSID é 4E3C66D5-58D4-491E-A7D4-64AF99AF6E8B. Você nunca deve alterar esse valor.

## <a name="_assemblylocation"></a>\_AssemblyLocation

Essa propriedade contém uma cadeia de caracteres que fornece detalhes sobre o manifesto de implantação para a personalização. Para obter mais informações sobre manifestos, consulte [manifestos de aplicativo e implantação em soluções do Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).

 O \_ valor da propriedade AssemblyLocation pode ter formatos diferentes, dependendo de como a solução é implantada:

- Se a solução for publicada para ser instalada a partir de um site, um caminho UNC ou uma unidade de CD ou USB, a propriedade _AssemblyLocation terá o formato *DeploymentManifestPath* | *SolutionID*. A cadeia de caracteres a seguir é um exemplo:

     file://deployserver/MyShare/ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9

- Se você estiver executando ou Depurando a solução do Visual Studio, a propriedade _AssemblyLocation terá o formato *DeploymentManifestName* | *SolutionID*| vstolocal. A cadeia de caracteres a seguir é um exemplo:

     ExcelWorkbook1. vsto | 74744e4b-e4d6-41eb-84f7-ad20346fe2d9 | vstolocal

  O *SolutionID* é um GUID que o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] usa para identificar a solução. O *SolutionID* é gerado automaticamente quando você cria o projeto. O termo **vstolocal** indica para o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] que o assembly deve ser carregado da mesma pasta que o documento.

## <a name="see-also"></a>Confira também

- [Arquitetura de soluções do Office no Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Arquitetura de personalizações em nível de documento](../vsto/architecture-of-document-level-customizations.md)
- [Manifestos de aplicativo e implantação em soluções do Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [Como publicar uma solução do Office usando o ClickOnce](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
- [Como: criar e modificar propriedades de documento personalizadas](../vsto/how-to-create-and-modify-custom-document-properties.md)
