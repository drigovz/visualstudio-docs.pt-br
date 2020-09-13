---
title: Registrar extensões de nome de arquivo para IDEs lado a lado
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c5ebedd2861ca96d1ad96c74a54da06578d33960
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036945"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>Registrar extensões de nome de arquivo para implantações lado a lado
Para o VSPackages implantado em um ambiente lado a lado, você deve registrar extensões de nome de arquivo para associar os arquivos com a versão correta do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . A menos que você use uma extensão de nome de arquivo específica de versão, o registro permite que os usuários abram o projeto e os arquivos de item de projeto na versão apropriada do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="in-this-section"></a>Nesta seção
- [Sobre extensões de nome de arquivo](../extensibility/about-file-name-extensions.md) Discute como as extensões de nome de arquivo são registradas.

- [Especificar manipuladores de arquivo para extensões de nome de arquivo](../extensibility/specifying-file-handlers-for-file-name-extensions.md) Fornece informações sobre como registrar os aplicativos que podem abrir, editar e assim por diante, uma extensão de nome de arquivo específica.

- [Registrar verbos para extensões de nome de arquivo](../extensibility/registering-verbs-for-file-name-extensions.md) Discute como registrar verbos.

- [Gerenciar associações de arquivos lado a lado](../extensibility/managing-side-by-side-file-associations.md) Discute como lidar com instalações lado a lado nas quais uma versão específica do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] deve ser chamada para abrir um arquivo.

## <a name="related-sections"></a>Seções relacionadas
- [Suporte a várias versões do Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md) Descreve problemas relacionados a várias versões do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e seu VSPackage durante o desenvolvimento e a implantação para os usuários finais.
