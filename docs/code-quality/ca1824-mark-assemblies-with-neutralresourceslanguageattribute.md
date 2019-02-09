---
title: 'CA1824: Marque assemblies com NeutralResourcesLanguageAttribute'
ms.date: 03/29/2018
ms.topic: reference
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40cb2a3674884a9fb4f1449c9afa2e0a2d27050f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55919138"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824: Marque assemblies com NeutralResourcesLanguageAttribute

|||
|-|-|
|NomeDoTipo|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|Categoria|Microsoft.Performance|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa

Um assembly contém um **ResX**-com base em recursos, mas não tem o <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> aplicado a ele.

## <a name="rule-description"></a>Descrição da regra

O <xref:System.Resources.NeutralResourcesLanguageAttribute> atributo informa o Gerenciador de recursos da cultura padrão de um aplicativo. Se os recursos da cultura padrão são inseridos no assembly de principal do aplicativo, e <xref:System.Resources.ResourceManager> tem que recuperar os recursos que pertencem à mesma cultura que a cultura padrão, o <xref:System.Resources.ResourceManager> usa automaticamente os recursos localizados no assembly principal em vez de procurar por um assembly satélite. Isso ignora a investigação de assembly usual, melhora o desempenho da pesquisa para o primeiro recurso de carga e pode reduzir o conjunto de trabalho.

> [!TIP]
> Ver [empacotamento e implantação de recursos](/dotnet/framework/resources/packaging-and-deploying-resources-in-desktop-apps) para o processo que <xref:System.Resources.ResourceManager> usa para investigar para arquivos de recurso.

## <a name="fix-violations"></a>Corrigir violações

Para corrigir uma violação dessa regra, adicione o atributo ao assembly e especificar o idioma dos recursos de cultura neutra.

### <a name="to-specify-the-neutral-language-for-resources"></a>Para especificar o idioma neutro para recursos

1. Na **Gerenciador de soluções**, clique em seu projeto e, em seguida, selecione **propriedades**.

2. Selecione o **Application** guia e, em seguida, selecione **informações de Assembly**.

   > [!NOTE]
   > Se seu projeto é um projeto .NET Standard ou .NET Core, selecione a **pacote** guia.

3. Selecione o idioma do **idioma neutro** ou **linguagem de Assembly neutra** lista suspensa.

4. Selecione **OK**.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

É permitido para suprimir um aviso nessa regra. No entanto, pode prejudicar o desempenho da inicialização.

## <a name="see-also"></a>Consulte também

- <xref:System.Resources.NeutralResourcesLanguageAttribute>
- [Recursos em aplicativos da área de trabalho (.NET)](/dotnet/framework/resources/)
- [CA1703 - cadeias de caracteres de recurso devem ter grafia correta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [Ca1701 as - cadeia de caracteres de recurso palavras compostas devem ter maiusculas e minúsculas corretamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)