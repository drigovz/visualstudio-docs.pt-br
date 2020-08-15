---
title: Obtendo logs de build com o MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, logging
- logging [MSBuild]
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3dad3a9b157989ecf993cf951f91fc6296ecdf7
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238602"
---
# <a name="obtain-build-logs-with-msbuild"></a>Obter logs de build com o MSBuild

Usando opções com o MSBuild, você pode especificar quantos dados de build você deseja examinar e se deseja salvar os dados de build em um ou mais arquivos. Você também pode especificar um agente personalizado para coletar dados de build. Para saber mais sobre opções de linha de comando do MSBuild que este tópico não aborda, confira [Referência de linha de comando](../msbuild/msbuild-command-line-reference.md).

> [!NOTE]
> Se você compilar projetos usando o IDE do Visual Studio, poderá solucionar os builds examinando os logs de build. Para obter mais informações, consulte [Como exibir, salvar e configurar arquivos de log de build](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="set-the-level-of-detail"></a>Definir o nível de detalhes

 Quando você compila um projeto usando MSBuild sem especificar um nível de detalhamento, as seguintes informações aparecem no log de saída:

- Erros, avisos e mensagens que são classificados como altamente importante.

- Alguns eventos de status.

- Um resumo do build.

Usando a opção **-verbosity** (**-v**), você pode controlar a quantidade de dados exibida no log de saída. Para solucionar o problema, use um nível de detalhes de `detailed` (`d`) ou `diagnostic` (`diag`), que fornece o máximo de informações.

O processo de compilação pode ser mais lento quando você define o **-detalhamento** para `detailed` e ainda mais lento quando você define o **-verbos** para `diagnostic` .

```cmd
msbuild MyProject.proj -t:go -v:diag
```

### <a name="verbosity-settings"></a>Configurações de detalhes

A tabela a seguir mostra como os detalhes do log (valores de coluna) afetam quais tipos de mensagem (valores de linha) são registrados em log.

| Tipo de mensagem/detalhes              | Quiet | Minimal | Normal | Detalhado | Diagnostic |
|---------------------------------------|:-----:|:-------:|:------:|:--------:|:----------:|
| Errors                                |   ✅   |    ✅    |    ✅   |     ✅    |      ✅     |
| Avisos                              |   ✅   |    ✅    |    ✅   |     ✅    |      ✅     |
| Mensagens de alta prioridade              |       |    ✅    |    ✅   |     ✅    |      ✅     |
| Mensagens de prioridade normal           |       |         |    ✅   |     ✅    |      ✅     |
| Mensagens de baixa prioridade              |       |         |        |     ✅    |      ✅     |
| Informações adicionais do mecanismo MSBuild |       |         |        |          |      ✅     |

## <a name="save-the-build-log-to-a-file"></a>Salvar o log de compilação em um arquivo

Você pode usar a opção **-fileLogger** (**fl**) para salvar dados de build em um arquivo. O exemplo a seguir salva dados de build em um arquivo chamado *msbuild.log*.

```cmd
msbuild MyProject.proj -t:go -fileLogger
```

 No exemplo a seguir, o arquivo de log é denominado *MyProjectOutput.log* e o detalhamento da saída do log é definida como `diagnostic`. Você especifica essas duas configurações usando a opção **-fileLoggerParameters** ( `flp` ).

```cmd
msbuild MyProject.proj -t:go -fl -flp:logfile=MyProjectOutput.log;verbosity=diagnostic
```

 Para saber mais, confira [Referência de linha de comando](../msbuild/msbuild-command-line-reference.md).

## <a name="save-the-log-output-to-multiple-files"></a>Salvar a saída de log em vários arquivos

 O exemplo a seguir salva o log inteiro em *msbuild1.log*, apenas os erros em *JustErrors.log* e apenas os avisos em *JustWarnings.log*. O exemplo usa números de arquivo para cada um dos três arquivos. Os números de arquivo são especificados logo após as opções **-fl** e **-flp** (por exemplo, `-fl1` e `-flp1`).

 As opções **-fileLoggerParameters** ( `flp` ) para os arquivos 2 e 3 especificam o que nomear cada arquivo e o que incluir em cada arquivo. Nenhum nome foi especificado para o arquivo 1, então o nome padrão de *msbuild1.log* é usado.

```cmd
msbuild MyProject.proj -t:go -fl1 -fl2 -fl3 -flp2:logfile=JustErrors.log;errorsonly -flp3:logfile=JustWarnings.log;warningsonly
```

 Para saber mais, confira [Referência de linha de comando](../msbuild/msbuild-command-line-reference.md).

## <a name="save-a-binary-log"></a>Salvar um log binário

Você pode salvar o log no formato binário compactado usando a opção **-binaryLogger** (**BL**). Esse log inclui uma descrição detalhada do processo de build e pode ser lido por algumas ferramentas de análise de log.

No exemplo a seguir, é criado um arquivo de log binário com o nome *binarylogfilename*.

```cmd
-bl:binarylogfilename.binlog
```

Para saber mais, confira [Referência de linha de comando](../msbuild/msbuild-command-line-reference.md).

## <a name="use-a-custom-logger"></a>Usar um agente personalizado

 Você pode escrever seu próprio agente por meio da criação de um tipo gerenciado que implementa a interface <xref:Microsoft.Build.Framework.ILogger>. Você pode usar um agente personalizado, por exemplo, para enviar erros de build por email, registrá-los em um banco de dados ou em um arquivo XML. Para saber mais, confira [Agentes de build](../msbuild/build-loggers.md).

 Na linha de comando do MSBuild, você especifica o agente de log personalizado usando a opção **-logger** . Você também pode usar a opção **-noconsolelogger** para desabilitar o agente de log de console padrão.

## <a name="see-also"></a>Consulte também

- <xref:Microsoft.Build.Framework.LoggerVerbosity>
- [Agentes de build](../msbuild/build-loggers.md)
- [Registrando em log em um ambiente multiprocessador](../msbuild/logging-in-a-multi-processor-environment.md)
- [Como criar agentes de encaminhamento](../msbuild/creating-forwarding-loggers.md)
- [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)
