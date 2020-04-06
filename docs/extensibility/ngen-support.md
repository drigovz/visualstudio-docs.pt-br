---
title: Suporte ngen em VSIX v3 | Microsoft Docs
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb75b9256ca937106235fa7a7d66d9cec71c9c60
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702407"
---
# <a name="ngen-support-in-vsix-v3"></a>Suporte a NGen no VSIX v3

Com o Visual Studio 2017 e o novo formato de manifesto de extensão VSIX v3 (versão 3), os desenvolvedores de extensão agora podem "ngen" seus conjuntos no momento da instalação.

Abaixo está um trecho do MSDN que explica o que "ngen" faz:

>O Gerador de Imagens Nativas (*Ngen.exe*) é uma ferramenta que melhora o desempenho de aplicativos gerenciados. *O Ngen.exe* cria imagens nativas, que são arquivos contendo código de máquina específico do processador compilado, e as instala no cache de imagem nativo no computador local. O runtime pode usar imagens nativas do cache em vez de usar o compilador JIT (Just-In-Time) para compilar o assembly original.
>
>de [Ngen.exe (Native Image Generator)](/dotnet/framework/tools/ngen-exe-native-image-generator)

Para "ngen" um conjunto, o VSIX deve ser instalado "por instância por máquina". Isso pode ser ativado verificando a caixa de seleção "todos os usuários" no `extension.vsixmanifest` designer:

![verificar todos os usuários](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Como ativar o Ngen

Para habilitar ngen para um conjunto, você pode usar a janela **Propriedades** no Visual Studio.

Existem 4 propriedades que podem ser definidas:

1. **Ngen** (Boolean) - Se for verdade, o instalador do Visual Studio "ngen" a montagem.
2. **Aplicativo Ngen** (string) - O Ngen oferece a oportunidade de usar o arquivo *app.config* de um aplicativo para resolver dependências de montagem. Esse valor deve ser definido como um aplicativo cujo *app.config* você deseja usar (em relação ao diretório de instalação do Visual Studio).
3. **Ngen Architecture** (enum) - A arquitetura para compilar nativamente sua montagem. As opções são: a. Não especificado b. X86 c. X64 d. Todos
4. **Ngen Priority** (inteiro entre 1 e 3) - O nível de Prioridade ngen é documentado nos [níveis de prioridade de Ngen.exe](/dotnet/framework/tools/ngen-exe-native-image-generator#priority-levels).

Aqui está uma olhada na janela **Propriedades** em ação:

![ngen em propriedades](media/ngen-in-properties.png)

Isso adicionará metadados à referência do projeto dentro do arquivo *.csproj* do projeto VSIX:

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
> Você pode editar o arquivo .csproj diretamente, se preferir.

## <a name="extra-information"></a>Informações extras

As alterações do designer de propriedades se aplicam a mais do que apenas referências de projeto; você pode definir os metadados ngen para itens dentro do seu projeto também (usando os mesmos métodos descritos acima) desde que os itens sejam conjuntos .NET.
