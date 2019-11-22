---
title: Criando um pacote de Windows Installer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 58529dabbb52ceb751c67be24beb1d21285a1de6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301131"
---
# <a name="authoring-a-windows-installer-package"></a>Criação de um pacote do Windows Installer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Os dados orientam o modelo de Windows Installer. Em vez de escrever um script de procedimento para copiar arquivos e gravar entradas do registro, por exemplo, crie linhas e colunas em tabelas de banco de dados que contenham arquivos de registro e arquivo.  
  
## <a name="database-entries"></a>Entradas de banco de dados  
 Para instalar um VSPackage, um pacote de Windows Installer deve conter entradas de banco de dados para executar as seguintes tarefas:  
  
- Pesquise o sistema para localizar as versões do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] que seu VSPackage dá suporte (usando Windows Installer tabelas que incluem AppSearch, CompLocator, RegLocator, DrLocator e Signature).  
  
- Cancele a instalação se nenhuma versão com suporte do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] estiver instalada ou se outro requisito de sistema do VSPackage não for atendido (usando a tabela LaunchCondition).  
  
- Instale o VSPackage e os arquivos dependentes (usando o diretório, o componente e as tabelas de arquivos).  
  
- Adicione as informações apropriadas para o VSPackage ao registro (usando a tabela de registro).  
  
- Integre o VSPackage em [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] chamando **devenv. exe/setup** (usando a tabela CustomAction).  
  
  Para obter mais informações, consulte [Windows Installer](https://msdn.microsoft.com/library/cc185688\(VS.85\).aspx).  
  
## <a name="setup-tools"></a>Ferramentas de instalação  
 Uma variedade de ferramentas de instalação de terceiros fornece um ambiente de desenvolvimento para pacotes Windows Installer. Duas ferramentas gratuitas são as seguintes:  
  
- InstallShield Limited Edition  
  
   Você pode obter uma versão limitada do InstallShield por meio da caixa de diálogo **novo projeto** do Visual Studio. Expanda **outros tipos de projeto** e, em seguida, selecione **instalação e implantação**. Selecione o modelo do InstallShield.  
  
- Conjunto de Ferramentas XML do Windows Installer  
  
   O conjunto de ferramentas cria pacotes de Windows Installer de arquivos de origem XML. O conjunto de ferramentas é um projeto de código-fonte aberto da Microsoft. Você pode baixar o código-fonte e os executáveis de [http://sourceforge.net/projects/wix](https://sourceforge.net/projects/wix/).  
  
  Para produtos comerciais que se integram ao [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] usando o [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], consulte [https://marketplace.visualstudio.com/](https://marketplace.visualstudio.com/).  
  
## <a name="see-also"></a>Consulte também  
 [Instalar VSPackages com o Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
