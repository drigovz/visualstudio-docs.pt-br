---
title: Instalando fora da pasta de extensões com VSIX v3 | Microsoft Docs
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa2c7d97dda9bba139ec613b367eedbc6307848a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700177"
---
# <a name="install-outside-the-extensions-folder"></a>Instalar fora da pasta de extensões

Começando com o Visual Studio 2017 e o VSIX v3 (versão 3), os ativos de extensão podem ser instalados fora da pasta de extensões. Atualmente, os seguintes locais estão habilitados como locais de instalação válidos (onde [INSTALLDIR] é mapeado para o diretório de instalação da instância do Visual Studio):

* [INSTALLDIR]\MSBuild
* [INSTALLDIR]\Xml\Schemas
* [INSTALLDIR]\Common7\IDE\PublicAssemblies
* [INSTALLDIR]\Licenças
* [INSTALLDIR]\Common7\IDE\ReferenceAssemblies
* [INSTALLDIR]\Common7\IDE\RemoteDeDe
* [INSTALLDIR]\Common7\IDE\VC\VCTargets (suportado apenas para o Visual Studio 2017; preterido para o Visual Studio 2019 e posterior)

> [!NOTE]
> O formato VSIX não permite que você instale fora da estrutura de pasta de instalação do Visual Studio. 

Para suportar a instalação nesses diretórios, o VSIX deve ser instalado "por instância por máquina". Isso pode ser ativado verificando a caixa de seleção "todos os usuários" no extension.vsixmanifest designer:

![verificar todos os usuários](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Como definir o InstallRoot

Para definir os diretórios de instalação, você pode usar a janela **Propriedades** no Visual Studio. Por exemplo, você `InstallRoot` pode definir a propriedade de uma referência de projeto a um dos locais acima:

![instalar propriedades radiculares](media/install-root-properties.png)

Isso adicionará alguns metadados à propriedade correspondente `ProjectReference` dentro do arquivo .csproj do projeto VSIX:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

> [!NOTE]
> Você pode editar o arquivo .csproj diretamente, se preferir.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Como definir um subcaminho sob o InstallRoot

Se você quiser instalar em um subcaminho abaixo do `InstallRoot`, você `VsixSubPath` pode fazê-lo definindo a propriedade assim como a `InstallRoot` propriedade. Por exemplo, digamos que queremos que a saída da referência do projeto seja instalada em '[INSTALLDIR]\MSBuild\MyCompany\MySDK\1.0'. Podemos fazer isso facilmente com o designer de imóveis:

![definir subcaminho](media/set-subpath.png)

As alterações .csproj correspondentes serão assim:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Informações extras

As alterações do designer de propriedades se aplicam a mais do que apenas referências de projeto; você pode `InstallRoot` definir os metadados para itens dentro do seu projeto também (usando os mesmos métodos descritos acima).
