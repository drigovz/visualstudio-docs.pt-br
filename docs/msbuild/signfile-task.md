---
title: Tarefa SignFile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#SignFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, SignFile task
- SignFile task [MSBuild]
ms.assetid: edef1819-ddeb-4e09-95de-fc7063ba9388
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5adc16bf0ded8171009c31d96227daa0474ebbf5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53847211"
---
# <a name="signfile-task"></a>Tarefa SignFile

Assina o arquivo especificado usando o certificado especificado.
  
## <a name="parameters"></a>Parâmetros

 A tabela a seguir descreve os parâmetros da tarefa `SignFile`.
  
 Observe que os certificados SHA-256 são permitidos apenas em computadores que tenham o .NET 4.5 e superior.
  
> [!WARNING]
> A partir do Visual Studio 2013 Atualização 3, essa tarefa tem uma nova assinatura que permite que você especifique a versão da estrutura de destino do arquivo. Você é incentivado a usar a nova assinatura sempre que possível, pois o processo do MSBuild usa hashes SHA-256 somente quando a estrutura de destino for .NET 4.5 ou superior. Se a estrutura de destino for .NET 4.0 ou abaixo, o hash SHA-256 não será usado.
  
|Parâmetro|Descrição|
|---------------|-----------------|
|`CertificateThumbprint`|Parâmetro `String` obrigatório.<br /><br /> Especifica o certificado a ser usado para a assinatura. Esse certificado deve estar no repositório pessoal do usuário atual.|
|`SigningTarget`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem> obrigatório.<br /><br /> Especifica os arquivos a serem assinados com o certificado.|
|`TimestampUrl`|Parâmetro `String` opcional.<br /><br /> Especifica a URL de um servidor de carimbo de data/hora.|
|`TargetFrameworkVersion`|A versão do .NET Framework que é usada para o destino.|
  
## <a name="remarks"></a>Comentários

 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, confira [Classe base Task](../msbuild/task-base-class.md).
  
## <a name="example"></a>Exemplo

 O exemplo a seguir usa a tarefa `SignFile` para assinar os arquivos especificados na coleção de itens `FilesToSign` com o certificado especificado pela propriedade `Certificate`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <FileToSign Include="File.exe" />
    </ItemGroup>
    <PropertyGroup>
        <Certificate>Cert.cer</Certificate>
    </PropertyGroup>
    <Target Name="Sign">
        <SignFile
            CertificateThumbprint="$(CertificateThumbprint)"
            SigningTarget="@(FileToSign)"
            TargetFrameworkVersion="v4.5" />
    </Target>
</Project>
```

> [!NOTE]
> A impressão digital do certificado é o hash SHA-1 do certificado. Para saber mais, confira [Obter o hash SHA-1 de um certificado de autoridade de certificação raiz confiável](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc733076\(v\=ws.10\)). Se você copiar e colar a impressão digital dos detalhes do certificado, não inclua o caractere invisível extra (3F), que pode impedir `SignFile` de encontrar o certificado.
  
## <a name="see-also"></a>Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Tarefas](../msbuild/msbuild-tasks.md)