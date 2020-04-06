---
title: Manifesto de Recursos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb853963cc5ca6fbe6080249daa8fcf9c08bf943
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707274"
---
# <a name="manifest-from-resources"></a>Manifest from Resources
A ferramenta Manifest from Resources é um aplicativo de console que pega uma lista de recursos de imagem (.png ou arquivos .xaml) e gera um arquivo .imagemanifest que permite que essas imagens sejam usadas com o Visual Studio Image Service. Além disso, esta ferramenta pode ser usada para adicionar imagens a um manifesto .imageexistente. Esta ferramenta é útil para adicionar suporte a alta DPI e tema para imagens a uma extensão do Visual Studio. O arquivo .imagemanifest gerado deve ser incluído e implantado como parte de uma extensão do Visual Studio (.vsix).

## <a name="how-to-use-the-tool"></a>Como usar a ferramenta
 **Sintaxe**

 ManifestFromResources /resources:\<Dir1>; \<Img1> /montagem:\< \<AssemblyName> Optional Args>

 **Argumentos**

||||
|-|-|-|
|**Nome do switch**|**Observações**|**Obrigatório ou opcional**|
|/recursos|Uma lista delimitada de imagens ou diretórios em ponto e vírgula. Esta lista deve conter sempre a lista completa de imagens que estarão no manifesto. Se apenas uma lista parcial for dada, as entradas não incluídas serão perdidas.<br /><br /> Se um determinado arquivo de recurso for uma tira de imagem, a ferramenta irá dividi-lo em imagens separadas antes de adicionar cada subimagem ao manifesto.<br /><br /> Se a imagem for um arquivo .png, recomendamos que você forme o nome assim para \<que a ferramenta possa preencher os atributos certos para a imagem: Nome>. \<Largura>. \<Altura>.png.|Obrigatório|
|/montagem|O nome da montagem gerenciada (sem incluir a extensão) ou o caminho de tempo de execução da montagem nativa que hospeda os recursos (em relação ao local de execução do manifesto).|Obrigatório|
|/manifest|O nome a dar ao arquivo .imagemanifest gerado. Isso também pode incluir um caminho absoluto ou relativo para criar o arquivo em um local diferente. O nome padrão corresponde ao nome do conjunto.<br /><br /> Padrão: \<Diretório atual \\>\><Assembly .imagemanifest|Opcional|
|/guidName|O nome para dar ao símbolo GUID para todas as imagens no manifesto gerado.<br /><br /> Padrão: AssetsGuid|Opcional|
|/rootPath|O caminho raiz que precisa ser desmontado antes de criar URIs de recurso gerenciados. (Este sinalizador é para ajudar nos casos em que a ferramenta erra o caminho uri relativo, fazendo com que os recursos não sejam carregados.)<br /><br /> Padrão: \<diretório atual>|Opcional|
|/recursive|A configuração deste sinalizador diz à ferramenta para pesquisar recursivamente quaisquer diretórios no argumento /resources. Omitir esta bandeira resultará em uma busca de diretórios somente de alto nível.|Opcional|
|/isNative|Defina esta bandeira quando o argumento de montagem for um caminho para uma montagem nativa. Omita esta bandeira quando o argumento de montagem é o nome de uma assembléia gerenciada. (Consulte a seção Notas para obter informações adicionais sobre esta bandeira.)|Opcional|
|/newGuids|A configuração deste sinalizador diz à ferramenta para criar um novo valor para o símbolo GUID das imagens em vez de fundir o do manifesto existente.|Opcional|
|/newIds|A configuração deste sinalizador diz à ferramenta para criar novos valores de símbolo de ID para cada imagem em vez de mesclar valores do manifesto existente.|Opcional|
|/noLogo|A configuração deste sinalizador impede a impressão de informações sobre produtos e direitos autorais.|Opcional|
|/?|Imprima informações de ajuda.|Opcional|
|/help|Imprima informações de ajuda.|Opcional|

 **Exemplos**

- ManifestFromResources /resources:D:\Images /assembly:My.Assembly.Name /isNative

- ManifestFromResources /resources:D:\Images\Image1.png;D:\Image1.xaml /assembly:My.Assembly.Name /manifest:MyImageManifest.imagemanifest

- ManifestFromResources /resources:D:\Images\Image1.png;D:\Image1.xaml /assembly:My.Assembly.Name /guidName:MyImages /newGuids /newIds

## <a name="notes"></a>Observações

- A ferramenta suporta apenas arquivos .png e .xaml. Qualquer outro tipo de imagem ou arquivo será ignorado. Um aviso é gerado para todos os tipos não suportados encontrados durante a análise dos recursos. Se nenhuma imagem suportada for encontrada quando a ferramenta estiver terminada parentando os recursos, um erro será gerado

- Seguindo o formato sugerido para imagens .png, a ferramenta definirá o valor de tamanho/dimensão para o .png para o tamanho especificado pelo formato, mesmo que difere do tamanho real da imagem.

- O formato largura/altura pode ser omitido para imagens .png, mas a ferramenta lerá a largura/altura real da imagem e as usará para o valor de tamanho/dimensão da imagem.

- Executar esta ferramenta na mesma faixa de imagem várias vezes para o mesmo manifesto .imageresultará em entradas de manifesto duplicadas, porque a ferramenta tenta dividir a faixa de imagem em imagens autônomas e adicioná-la ao manifesto existente.

- A fusão (omitindo /newGuids ou /newIds) só deve ser feita para manifestos gerados por ferramentas. Manifestações que foram personalizadas ou geradas por outros meios podem não ser mescladas corretamente.

- Os manifestos gerados para assembléias nativas podem precisar ser editados à mão após a geração para fazer com que os símbolos de ID correspondam aos IDs de recursos do arquivo .rc da montagem nativa.

## <a name="sample-output"></a>Saída de exemplo
 **Manifesto de imagem simples**

 Um manifesto de imagem será semelhante a este arquivo .xml:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- This file was generated by the ManifestFromResources tool.-->
<!-- Version: 14.0.15197 -->
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">
  <Symbols>
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/Images" />
    <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />
    <ID Name="MyImage" Value="0" />
  </Symbols>
  <Images>
    <Image Guid="$(AssetsGuid)" ID="$(MyImage)">
      <Source Uri="$(Resources)/Xaml/MyImage.xaml" />
      <Source Uri="$(Resources)/Png/MyImage.16.16.png">
        <Size Value="16" />
      </Source>
    </Image>
  </Images>
  <ImageLists />
</ImageManifest>
```

 **Manifesto de imagem para uma tira de imagem**

 Um manifesto de imagem para uma tira de imagem será semelhante a este arquivo .xml:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- This file was generated by the ManifestFromResources tool.-->
<!-- Version: 14.0.15197 -->
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">
  <Symbols>
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" />
    <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />
    <ID Name="MyImageStrip_0" Value="1" />
    <ID Name="MyImageStrip_1" Value="2" />
    <ID Name="MyImageStrip" Value="3" />
  </Symbols>
  <Images>
    <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)">
      <Source Uri="$(Resources)/MyImageStrip_0.png">
        <Size Value="16" />
      </Source>
    </Image>
    <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)">
      <Source Uri="$(Resources)/MyImageStrip_1.png">
        <Size Value="16" />
      </Source>
    </Image>
  </Images>
  <ImageLists>
    <ImageList Guid="$(AssetsGuid)" ID="$(MyImageStrip)">
      <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)" />
      <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)" />
    </ImageList>
  </ImageLists>
</ImageManifest>
```

 **Manifesto de imagem para recursos de imagem de montagem nativa**

 Um manifesto de imagem para imagens nativas será semelhante a este arquivo .xml:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- This file was generated by the ManifestFromResources tool.-->
<!-- Version: 14.0.15198 -->
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">
  <Symbols>
    <String Name="Resources" Value="..\Assembly\Folder\My.Assembly.Name" />
    <Guid Name="AssetsGuid" Value="{442d8739-efde-46a4-8f29-e3a1e5e7f8b4}" />
    <ID Name="MyImage1" Value="0" />
    <ID Name="MyImage2" Value="1" />
  </Symbols>
  <Images>
    <Image Guid="$(AssetsGuid)" ID="$(MyImage1)">
      <Source Uri="$(Resources)">
        <Size Value="16" />
        <NativeResource ID="$(MyImage1)" Type="PNG" />
      </Source>
    </Image>
    <Image Guid="$(AssetsGuid)" ID="$(MyImage2)">
      <Source Uri="$(Resources)">
        <Size Value="16" />
        <NativeResource ID="$(MyImage2)" Type="PNG" />
      </Source>
    </Image>
  </Images>
  <ImageLists />
</ImageManifest>
```
