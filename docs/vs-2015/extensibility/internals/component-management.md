---
title: Gerenciamento de componentes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 56a110f382d0b182eed0ea1a95cd4dabf2877037
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191857"
---
# <a name="component-management"></a>Gerenciamento de componentes
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

As unidades de tarefas no Windows Installer são chamadas de componentes Windows Installer (às vezes chamados de WICs ou apenas componentes). Um GUID identifica cada WIC, que é a unidade básica de instalação e a contagem de referência para as configurações que usam Windows Installer.  
  
 Embora você possa usar vários produtos para criar o instalador do VSPackage, essa discussão pressupõe o uso de arquivos Windows Installer (. msi). Ao criar o instalador, você deve gerenciar corretamente a implantação de arquivos para que a contagem de referência correta ocorra em todos os momentos. Consequentemente, versões diferentes do seu produto não interferem ou se interrompem em uma combinação de cenários de instalação e desinstalação.  
  
 No Windows Installer, a contagem de referência ocorre no nível do componente. Você deve organizar seus recursos cuidadosamente — arquivos, entradas de registro e assim por diante — em componentes. Há outros níveis de organização, como módulos, recursos e produtos, que podem ajudar em cenários diferentes. Para obter mais informações, consulte [noções básicas do Windows Installer](../../extensibility/internals/windows-installer-basics.md).  
  
## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Diretrizes de criação da instalação para instalação lado a lado  
  
- Crie arquivos e chaves do registro que são compartilhados entre versões em seus próprios componentes.  
  
     Isso permite que você os consuma facilmente na próxima versão. Por exemplo, as bibliotecas de tipos que são registradas globalmente, extensões de arquivo, outros itens registrados em HKEY_CLASSES_ROOT e assim por diante.  
  
- Agrupe componentes compartilhados em módulos de mesclagem separados.  
  
     Isso ajuda você a criar corretamente para a movimentação lado a lado.  
  
- Instale arquivos compartilhados e chaves do registro usando os mesmos componentes Windows Installer entre versões.  
  
     Se você usar um componente diferente, os arquivos e as entradas do registro serão desinstalados quando um VSPackage com versão for desinstalado, mas outro VSPackage ainda estiver instalado.  
  
- Não misture itens com versão e compartilhados no mesmo componente.  
  
     Isso torna impossível instalar itens compartilhados em um local global e itens com controle de versão em locais isolados.  
  
- Não têm chaves de registro compartilhadas que apontam para arquivos com versão.  
  
     Se você fizer isso, as chaves compartilhadas serão substituídas quando outro VSPackage com versão for instalado. Depois de remover a segunda versão, o arquivo para o qual a chave está apontando é desaparecido.  
  
## <a name="see-also"></a>Consulte Também  
 [Escolhendo entre VSPackages compartilhadas e com controle de versão](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Cenários de instalação do VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)
