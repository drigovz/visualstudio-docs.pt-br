---
title: Comando Shell
description: Saiba mais sobre o comando do Shell e como ele inicia programas executáveis no Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- tools.shell
helpviewer_keywords:
- exe files
- Shell command
- Tools.Shell command
- executables, running from Visual Studio
- .exe files
- Shell, launching exe files
- Visual Studio, executables from
ms.assetid: 737fda23-b852-45c4-a9fe-41cbce6ba70f
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a6197201ed35520ba8d362b6aa448fe625a2fe3a
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616362"
---
# <a name="shell-command"></a>Comando Shell
Inicia programas executáveis de dentro do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="syntax"></a>Sintaxe

```cmd
Tools.Shell [/command] [/output] [/dir:folder] path [args]
```

## <a name="arguments"></a>Argumentos
`path`

Obrigatórios. O caminho e o nome do arquivo a ser executado ou o documento a ser aberto. Será necessário um caminho completo se o arquivo especificado não estiver em um dos diretórios na variável de ambiente PATH.

`args`

Opcional. Quaisquer argumentos a serem passados para o programa invocado.

## <a name="switches"></a>Comutadores
/commandwindow [ou] /command [ou] /c [ou] /cmd

Opcional. Especifica que a saída para o executável é exibida na janela **Comando**.

/dir:`folder` [ou] /d: `folder`

Opcional. Especifica o diretório de trabalho a ser definido quando o programa é executado.

/outputwindow [ou] /output [ou] /out [ou] /o

Opcional. Especifica que a saída para o executável é exibida na Janela de **Saída**.

## <a name="remarks"></a>Comentários
As opções /dir /o /c devem ser especificadas imediatamente após `Tools.Shell`. Qualquer coisa especificada após o nome do executável é passada para ele como argumentos de linha de comando.

O alias predefinido `Shell` pode ser usado no lugar de `Tools.Shell`.

> [!CAUTION]
> Se o argumento `path` fornecer o caminho de diretório, bem como o nome de arquivo, é necessário colocar o nome do caminho inteiro em aspas literais ("""), conforme o seguinte:

```cmd
Tools.Shell """C:\Program Files\SomeFile.exe"""
```

Cada conjunto de três aspas duplas (""") é interpretado pelo processador `Shell` como um único caractere de aspas duplas. Portanto, o exemplo anterior, na verdade, passa a seguinte cadeia de caracteres de caminho para o comando `Shell`:

```cmd
"C:\Program Files\SomeFile.exe"
```

> [!CAUTION]
> Se você não colocar a cadeia de caracteres de caminho em aspas literais ("""), o Windows usará somente a parte da cadeia de caracteres que vai até o primeiro espaço. Por exemplo, se a cadeia de caracteres de caminho acima não tivesse sido colocada adequadamente entre aspas, Windows pareceria um arquivo denominado “Programa” localizado no diretório raiz C:\. Se um arquivo executável C:\Program.exe estivesse mesmo disponível, e inclusive tivesse sido instalado por adulteração ilícita, o Windows tentaria executar esse programa no lugar do programa “c:\Arquivos de Programas\SomeFile.exe”.

## <a name="example"></a>Exemplo
O comando a seguir usa xcopy.exe para copiar o arquivo `MyText.txt` para a pasta `Text`. A saída de xcopy.exe é exibida na **Janela Comando** e na Janela de **Saída**.

```cmd
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt
```

## <a name="see-also"></a>Confira também

- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Janela de comando](../../ide/reference/command-window.md)
- [Janela de Saída](../../ide/reference/output-window.md)
- [Caixa Localizar/comando](../../ide/find-command-box.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
