---
title: Suporte a NGen no VSIX v3 | Microsoft Docs
description: Saiba como habilitar o gerador de imagem nativa, que é uma ferramenta que os desenvolvedores de extensão podem usar para melhorar o desempenho de aplicativos gerenciados.
ms.custom: SEO-VS-2020
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 064176a0a28e3621e796bf60ede552f9cda155b0
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97864034"
---
# <a name="ngen-support-in-vsix-v3"></a>Suporte a NGen no VSIX v3

Com o Visual Studio 2017 e o novo formato de manifesto de extensão do VSIX v3 (versão 3), os desenvolvedores de extensão agora podem "NGen" seus assemblies no momento da instalação.

Veja abaixo um trecho do MSDN que explica o que o "NGen" faz:

>O gerador de imagem nativa (*Ngen.exe*) é uma ferramenta que melhora o desempenho de aplicativos gerenciados. *Ngen.exe* cria imagens nativas, que são arquivos que contêm código de máquina compilado específico do processador e os instala no cache de imagem nativa no computador local. O runtime pode usar imagens nativas do cache em vez de usar o compilador JIT (Just-In-Time) para compilar o assembly original.
>
>de [Ngen.exe (gerador de imagem nativa)](/dotnet/framework/tools/ngen-exe-native-image-generator)

Para "NGen" um assembly, o VSIX deve ser instalado "por instância por máquina". Isso pode ser habilitado marcando a caixa de seleção "todos os usuários" no `extension.vsixmanifest` Designer:

![verificar todos os usuários](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Como habilitar o NGen

Para habilitar o NGen para um assembly, você pode usar a janela **Propriedades** no Visual Studio.

Há quatro propriedades que podem ser definidas:

1. **NGen** (booliano)-se verdadeiro, o instalador do Visual Studio irá "NGen" o assembly.
2. **Aplicativo NGen** (cadeia de caracteres)-o NGen fornece a oportunidade de usar o arquivo de *app.config* de um aplicativo para resolver dependências de assembly. Esse valor deve ser definido como um aplicativo cujo *app.config* você deseja usar (relativo ao diretório de instalação do Visual Studio).
3. **Arquitetura NGen** (enum)-a arquitetura para compilar nativamente seu assembly. As opções são: a. Não especificado b. X86 c. X64 d. Tudo
4. **Prioridade NGen** (inteiro entre 1 e 3)-o nível de prioridade NGen é documentado em [ níveis de prioridadeNgen.exe](/dotnet/framework/tools/ngen-exe-native-image-generator#priority-levels).

Aqui está uma olhada na janela **Propriedades** em ação:

![NGen nas propriedades](media/ngen-in-properties.png)

Isso adicionará metadados à referência do projeto dentro do arquivo *. csproj* do projeto VSIX:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
    <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
    <Name>ClassLibrary1</Name>
    <Ngen>True</Ngen>
    <NgenApplication>vsn.exe</NgenApplication>
    <NgenArchitecture>X86</NgenArchitecture>
    <NgenPriority>2</NgenPriority>
</ProjectReference>
```

> [!NOTE]
> Você pode editar o arquivo. csproj diretamente, se preferir.

## <a name="extra-information"></a>Informações adicionais

As alterações do designer de propriedade se aplicam a mais do que apenas referências de projeto; Você também pode definir os metadados do NGen para os itens dentro do seu projeto (usando os mesmos métodos descritos acima), desde que os itens sejam assemblies .NET.
