---
title: Autor de um pacote de instalador do Windows | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03d30c0e2b3b375e6e0efedddd3a017fbfb8646a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710033"
---
# <a name="author-a-windows-installer-package"></a>Autor de um pacote do Instalador do Windows
Os dados impulsionam o modelo do Instalador do Windows. Em vez de escrever um script processual para copiar arquivos e escrever entradas de registro, por exemplo, você escreve linhas e colunas em tabelas de banco de dados que contêm dados de arquivo e registro.

## <a name="database-entries"></a>Entradas de banco de dados
Para instalar um VSPackage, um pacote do Windows Installer deve conter entradas de banco de dados para executar as seguintes tarefas:

- Pesquise no sistema para [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] localizar as versões dos suportes do VSPackage (usando tabelas do Windows Installer que incluem AppSearch, CompLocator, RegLocator, DrLocator e Signature).

- Cancele a instalação se [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nenhuma versão suportada for instalada ou se outro requisito do sistema do VSPackage não for atendido (usando a tabela LaunchCondition).

- Instale o VSPackage e os arquivos dependentes (usando as tabelas de diretório, componente e arquivo).

- Adicione informações apropriadas para o VSPackage ao registro (usando a tabela Registro).

- Integre o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage ligando **para devenv.exe/setup** (usando a tabela CustomAction).

Para obter mais informações, consulte [o Instalador do Windows](/windows/desktop/Msi/windows-installer-portal).

## <a name="setup-tools"></a>Ferramentas de configuração
Uma variedade de ferramentas de configuração de terceiros fornece um ambiente de desenvolvimento para pacotes do Windows Installer. As seguintes ferramentas gratuitas estão disponíveis:

- Edição limitada do InstallShield

   Você pode obter uma versão limitada do InstallShield através da caixa de diálogo Visual Studio **New Project.** Expanda **outros tipos de projeto** e selecione **Configuração e Implantação**. Selecione o modelo InstallShield.

- Conjunto de ferramentas Do Windows Installer XML

   O conjunto de ferramentas Windows Installer XML (WiX) cria pacotes do Windows Installer a partir de arquivos de origem XML. O conjunto de ferramentas WiX é um projeto de código aberto da Microsoft. Você pode baixar o código-fonte e executáveis do conjunto de [ferramentas Wix](https://sourceforge.net/projects/wix/).

   Para produtos comerciais [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]se integram usando o , consulte [Visual Studio Marketplace](https://marketplace.visualstudio.com/).

## <a name="see-also"></a>Confira também
- [Instale pacotes VS com o instalador do Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
