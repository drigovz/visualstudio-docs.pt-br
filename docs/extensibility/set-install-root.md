---
title: Instalando fora da pasta de extensões VSIX v3 | Microsoft Docs
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d5fc36c1244edd0988b6b76f8106020369cd90b
ms.sourcegitcommit: da4079f5b6ec884baf3108cbd0519d20cb64c70b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67852191"
---
# <a name="install-outside-the-extensions-folder"></a>Instalar fora da pasta de extensões

Começando com o Visual Studio 2017 e VSIX v3 ativos de extensão (versão 3), pode ser instalado fora da pasta extensões. Atualmente, os locais a seguir são habilitados como locais de instalação válida (onde [INSTALLDIR] é mapeado para o diretório de instalação da instância do Visual Studio):

* [INSTALLDIR]\MSBuild
* [INSTALLDIR]\Xml\Schemas
* [INSTALLDIR]\Common7\IDE\PublicAssemblies
* [INSTALLDIR]\Licenses
* [INSTALLDIR]\Common7\IDE\ReferenceAssemblies
* [INSTALLDIR]\Common7\IDE\RemoteDebugger
* \Common7\IDE\VC\VCTargets [INSTALLDIR] (apenas com suporte para Visual Studio 2017; preteridas para Visual Studio de 2019 e posterior)

> [!NOTE]
> O formato VSIX não permite que você instale fora a estrutura de pasta de instalação do Visual Studio. 

Para dar suporte à instalação para esses diretórios, VSIX deve ser instalado "por instância por máquina". Isso pode ser habilitado marcando a caixa de seleção de "todos os usuários" no designer de vsixmanifest:

![Verifique todos os usuários](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Como definir a InstallRoot

Para definir os diretórios de instalação, você pode usar o **propriedades** janela no Visual Studio. Por exemplo, você pode definir o `InstallRoot` propriedade de uma referência de projeto para um dos locais acima:

![Propriedades de raiz de instalação](media/install-root-properties.png)

Isso adicionará alguns metadados para os respectivos `ProjectReference` propriedade dentro do arquivo. csproj do projeto VSIX:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

> [!NOTE]
> Você pode editar o arquivo. csproj diretamente, se você preferir.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Como definir um subcaminho sob a InstallRoot

Se você deseja instalar em um subcaminho sob a `InstallRoot`, você pode fazer isso definindo o `VsixSubPath` propriedade assim como o `InstallRoot` propriedade. Por exemplo, digamos que queremos que a saída da nossa referência de projeto para instalar em ' [INSTALLDIR]\MSBuild\MyCompany\MySDK\1.0'. Podemos fazer isso facilmente com o designer de propriedade:

![subcaminho do conjunto](media/set-subpath.png)

As alterações correspondentes de csproj terá esta aparência:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Informações adicionais

As alterações de propriedade designer se aplicam a mais do que apenas as referências de projeto; Você pode definir o `InstallRoot` metadados para os itens dentro de seu projeto também (usando os mesmos métodos descritos acima).
