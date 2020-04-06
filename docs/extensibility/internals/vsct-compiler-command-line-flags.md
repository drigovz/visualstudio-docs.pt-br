---
title: VsCT Compiler Command-Line Bandeiras | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e4ee29710049453c3163c366eccf96e257b6028d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703965"
---
# <a name="vsct-compiler-command-line-flags"></a>Sinalizadores de linha de comando do compilador VSCT
O compilador Visual Studio Command Table (VSCT) fornece switches de linha de comando para garantir uma compilação bem sucedida de arquivos .vsct.

## <a name="command-line-parameters"></a>Parâmetros da linha de comando
 Para visualizar a ajuda [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] básica do VSCT a partir de uma janela **de comando,** navegue até o caminho de instalação do *Visual Studio SDK*\VisualStudioIntegration\Tools\Bin\ pasta e digite:

```
vsct /?
```

 Isso retorna:

```
Microsoft (R) Visual Studio (R) Command Table Compiler Version 3.00.2000

Syntax: vsct <infile> [<outfile>] [-S[symbols file]] [-D<preprocessor-define>]*
[-I<include-path>]* [-L<language>] [-E[C|H|N]:<name>]

  -D    Specify any additional preprocessor defines
  -I    Indicate what additional include paths to send to the preprocessor
  -L    Specify the language to use when selecting strings
  -E    Emit C# objects in the specified namespace for command items,
        followed by [L|F|H|N]:<value>
        F = Name of the file to emit (used if -EL is provided)
        L = Name of a language providing a CodeDOM provider
        N = namespace (required if -EL is provided)
        H = C++ header
  -c    Clean build skipping dependency checks
  -v    Verbose output
```

> [!NOTE]
> Os caracteres - (traço) e / (barra para frente) são ambos aceitos notação para indicar parâmetros de linha de comando.

 Bandeiras aceitáveis e o que elas significam são as seguintes.

|Opção|Descrição|
|------------|-----------------|
|-d|Especifique quaisquer símbolos definidos adicionais.|
|-I|Indique os caminhos adicionais que devem ser usados ao resolver referências de arquivo.|
|-l|Especifique o nome da <xref:System.Globalization.CultureInfo> cultura, por exemplo "en-US".|
|-E|Emite objetos C# no espaço de nome especificado para itens de comando, seguido por [C&#124;H&#124;N]:*nome onde*C = C#, H = Cabeçalho C++, N = namespace. O namespace é necessário para C#.|
|-v|Saída verbose.|

 O switch -L instrui o compilador a selecionar um grupo de strings para produzir <xref:System.Globalization.CultureInfo> o arquivo binário .cto que corresponde ao nome da cultura dado. O nome de cultura especificado deve corresponder ao atributo Language de um ou mais [Elementos de Strings](../../extensibility/strings-element.md) no arquivo .vsct. Se um elemento Strings não tiver nenhum atributo de Linguagem, ele será herdado do [elemento CommandTable ( elemento de tabela de comando)](../../extensibility/commandtable-element.md)que contém.

 Um arquivo .vsct pode ter vários elementos de Strings, e cada um pode ter um atributo de Idioma diferente. A globalização é alcançada executando o compilador VSCT várias vezes e alterando o switch -L para cada nome de cultura.

 Se o nome de cultura dado pelo switch -L não corresponder ao atributo Language de qualquer elemento Strings, o compilador tentará corresponder ao idioma, e não à região. Por exemplo, se "en-US" não puder ser encontrado, o compilador tentará "en" em vez disso. Caso contrário, tentará a cultura atual do sistema operacional. Caso contrário, ele irá compilar o primeiro elemento Strings que encontrar.

 O switch -E pode ser usado para emitir um arquivo de cabeçalho no estilo C que contém os símbolos usados pela tabela de comando ou para emitir um arquivo C# que contenha objetos para os símbolos de comando.

 Os interruptores -D e -I têm a sintaxe das bandeiras de pré-processador Cl.exe C que têm o mesmo nome. -As definições d que têm o formato X=Y são \<usadas para `Condition` a expansão de testes de> definidos com base em XML em atributos. -Incluo caminhos \<usados \<para resolver as \<referências de>, Extern> e Bitmap>. Para obter mais informações, consulte a [referência do esquema VSCT XML](../../extensibility/vsct-xml-schema-reference.md).

 O compilador VSCT também pode descompilar um arquivo binário previamente construído. Para fazer isso, forneça um \<arquivo binário para o> de arquivo.   Se o arquivo binário foi produzido pelo compilador VSCT, ele terá seus símbolos já \<incorporados e produzirá saída com os nomes simbólicos em uma seção Símbolos> da saída. Se o binário foi produzido pelo compilador CTC, a saída conterá os GUIDs e IDs reais. Se o arquivo *.ctsym produzido pelas versões atuais do Ctc.exe estiver na mesma pasta que o arquivo de entrada binário, os símbolos serão carregados a partir desse arquivo e usados para saída.

## <a name="see-also"></a>Confira também
- [Arquivos .Vsct (Visual Studio Command Table)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Referência do esquema XML do VSCT](../../extensibility/vsct-xml-schema-reference.md)
- [Como os VSPackages adicionam elementos da interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
