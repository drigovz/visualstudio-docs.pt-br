---
title: Escolhendo o Diretório de Instalação para um VSPackage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b8391cbdd3a857ea4ebaf3a36655520935f1a128
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709755"
---
# <a name="choose-the-installation-directory-for-a-vspackage"></a>Escolha o diretório de instalação para um VSPackage
Um VSPackage e seus arquivos de suporte devem estar no sistema de arquivos de um usuário. A localização depende se o VSPackage é gerenciado ou não gerenciado, seu esquema de versão lado a lado e a escolha do usuário.

## <a name="unmanaged-vspackages"></a>Pacotes VS não gerenciados
 Um VSPackage não gerenciado é um servidor COM que pode ser instalado em qualquer local. Suas informações de registro devem refletir com precisão sua localização. A interface do usuário do instalador (UI) deve fornecer `ProgramFilesFolder` um local padrão como subdiretório do valor de propriedade do Windows Installer. Por exemplo:

*&lt;ProgramFilesfolder&gt;\\&lt;&gt;\\&lt;MyCompany MyVSPackageProduct&gt;\V1.0\\*

 O usuário deve ser autorizado a alterar o diretório padrão para acomodar usuários que mantêm uma pequena partição de inicialização e preferem instalar aplicativos e ferramentas em outro volume.

 Se o seu esquema lado a lado usar um VSPackage com versões, você pode usar subdiretórios para armazenar diferentes versões. Por exemplo:

 *&lt;ProgramFilesfolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2002\\*

 *&lt;ProgramFilesfolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2003\\*

 *&lt;ProgramFilesfolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2005\\*

## <a name="managed-vspackages"></a>VSPackages gerenciados
 Os VSPackages gerenciados também podem ser instalados em qualquer local. No entanto, você deve considerar sempre instalá-los no cache de montagem global (GAC) para reduzir os tempos de carga de montagem. Como os VSPackages gerenciados são sempre conjuntos com nome forte, instalá-los no GAC significa que a verificação de assinatura de nome forte leva apenas no momento da instalação. Conjuntos com nomes fortes instalados em outros lugares do sistema de arquivos devem ter suas assinaturas verificadas cada vez que são carregadas. Ao instalar vspackages gerenciados no GAC, use o interruptor **/conjunto** da ferramenta regpkg para gravar entradas de registro apontando para o nome forte do conjunto.

 Se você instalar VSPackages gerenciados em um local diferente do GAC, siga os conselhos anteriores dados para VSPackages não gerenciados para escolher hierarquias de diretório. Use o switch **/codebase** da ferramenta regpkg para gravar entradas de registro apontando para o caminho do conjunto VSPackage.

 Para obter mais informações, consulte [Registrar e cancelar o registro VSPackages](../../extensibility/registering-and-unregistering-vspackages.md).

## <a name="satellite-dlls"></a>DLLs satélites
 Por convenção, os DLLs de satélite VSPackage, que contêm recursos para um determinado local, estão localizados em subdiretórios do diretório *VSPackage.* Os subdiretórios correspondem aos valores de ID local (LCID).

 O artigo [Gerenciar VSPackages](../../extensibility/managing-vspackages.md) indica que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] as entradas de registro controlam onde realmente procura um DLL de satélite do VSPackage. No [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entanto, tenta carregar um DLL de satélite em um subdiretório nomeado para um valor LCID, na seguinte ordem:

1. LCID padrão (Visual Studio LCID; por exemplo, *\1033* para inglês)

2. LCID padrão com o sublinguagem padrão.

3. LCID padrão do sistema.

4. LCID padrão do sistema com a sublinguagem padrão.

5. Inglês americano (*.\1033* ou *.\0x409*).

Se o vsPackage DLL incluir recursos e a entrada de registro [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **SatelliteDll\DllName** for a ele, tente carregá-los na ordem acima.

## <a name="see-also"></a>Confira também
- [Escolha entre VSPackages compartilhados e versões](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [Gerenciar VSPackages](../../extensibility/managing-vspackages.md)
- [Gerenciar o registro do pacote](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
