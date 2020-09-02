---
title: Escolhendo o diretório de instalação para um VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c4100c045181f32e51abcc59116a69cad6cc33b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697240"
---
# <a name="choosing-the-installation-directory-for-a-vspackage"></a>Escolhendo o diretório de instalação de um VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Um VSPackage e seus arquivos de suporte devem estar no sistema de arquivos de um usuário. O local depende de o VSPackage ser gerenciado ou não gerenciado, seu esquema de controle de versão lado a lado e a escolha do usuário.  
  
## <a name="unmanaged-vspackages"></a>VSPackages não gerenciado  
 Um VSPackage não gerenciado é um servidor COM que pode ser instalado em qualquer local. Suas informações de registro devem refletir com precisão seu local. A interface do usuário do instalador deve fornecer um local padrão como um subdiretório da propriedade de Windows Installer ProgramFilesFolder. Por exemplo:  
  
 ProgramFilesFolder MyCompany\MyVSPackageProduct\V1.0\  
  
 O usuário deve ter permissão para alterar o diretório padrão para acomodar usuários que mantêm uma pequena partição de inicialização e preferem instalar aplicativos e ferramentas em outro volume.  
  
 Se o esquema lado a lado usar um VSPackage com controle de versão, você poderá usar subdiretórios para armazenar versões diferentes. Por exemplo:  
  
 ProgramFilesFolder MyCompany\MyVSPackageProduct\V1.0\2002\  
  
 ProgramFilesFolder MyCompany\MyVSPackageProduct\V1.0\2003\  
  
 ProgramFilesFolder MyCompany\MyVSPackageProduct\V1.0\2005\  
  
## <a name="managed-vspackages"></a>VSPackages gerenciados  
 O VSPackages gerenciado também pode ser instalado em qualquer local. No entanto, você deve considerar sempre instalá-los no GAC (cache de assembly global) para reduzir os tempos de carregamento do assembly. Como os VSPackages gerenciados são sempre assemblies com nomes fortes, instalá-los no GAC significa que a verificação de assinatura de nome forte leva apenas no momento da instalação. Os assemblies de nome forte instalados em outro lugar no sistema de arquivos devem ter suas assinaturas verificadas toda vez que forem carregados. Ao instalar o VSPackages gerenciado no GAC, use a opção **/assembly** da ferramenta regpkg para gravar entradas do registro apontando para o nome forte do assembly.  
  
 Se você instalar o VSPackages gerenciado em um local diferente do GAC, siga o aviso anterior fornecido para VSPackages não gerenciado para escolher hierarquias de diretório. Use a opção **/codebase** da ferramenta regpkg para gravar entradas do registro apontando para o caminho do assembly VSPackage.  
  
 Para obter mais informações, consulte [registrando e cancelando o registro de VSPackages](../../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="satellite-dlls"></a>DLLs satélites  
 Por convenção, as DLLs satélite VSPackage, que contêm recursos para uma localidade específica, estão localizadas em subdiretórios do diretório VSPackage. Os subdiretórios correspondem aos valores de LCID (ID de localidade).  
  
 O [Gerenciamento de VSPackages](../../extensibility/managing-vspackages.md) indica que as entradas do registro controlam onde [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] realmente procura pela DLL satélite de um VSPackage. No entanto, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] o tenta carregar uma DLL satélite em um subdiretório nomeado para um valor LCID, na seguinte ordem:  
  
1. LCID padrão (VS LCID, por exemplo, \ 1033 para inglês)  
  
2. LCID padrão com o subidioma padrão.  
  
3. LCID padrão do sistema.  
  
4. LCID padrão do sistema com o subidioma padrão.  
  
5. Inglês americano (. \ 1033 ou .\0x409).  
  
   Se a DLL VSPackage incluir recursos e os pontos de entrada do registro SatelliteDll\DllName, o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] tentará carregá-los na ordem acima.  
  
## <a name="see-also"></a>Consulte Também  
 [Escolhendo entre VSPackages compartilhadas e com controle de versão](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Gerenciando VSPackages](../../extensibility/managing-vspackages.md)   
 [Registro de pacote gerenciado](https://msdn.microsoft.com/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
