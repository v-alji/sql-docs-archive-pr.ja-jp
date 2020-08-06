---
title: 無効な文字とエスケープの規則 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, invalid characters
- FOR XML clause, escape rules
ms.assetid: f2e9b997-f400-4963-b225-59d46c6b93e8
author: rothja
ms.author: jroth
ms.openlocfilehash: 8624a31dea4e97e05da6d86c3c0c518b9c4d0aba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741661"
---
# <a name="invalid-characters-and-escape-rules"></a><span data-ttu-id="13d13-102">無効な文字とエスケープの規則</span><span class="sxs-lookup"><span data-stu-id="13d13-102">Invalid Characters and Escape Rules</span></span>
  <span data-ttu-id="13d13-103">このトピックでは、無効な XML 文字が FOR XML 句でどのように処理されるのかを説明し、XML 名では無効になる文字のエスケープの規則を示します。</span><span class="sxs-lookup"><span data-stu-id="13d13-103">This topic describes how invalid XML characters are handled by the FOR XML clause, and lists the escape rules for characters that are invalid in XML names.</span></span>  
  
## <a name="for-xml-and-invalid-characters"></a><span data-ttu-id="13d13-104">For XML と無効な文字</span><span class="sxs-lookup"><span data-stu-id="13d13-104">For XML and Invalid Characters</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="13d13-105">では、無効な XML 文字が TYPE ディレクティブの指定されていない FOR XML クエリの結果として返される場合、これらの文字をエンティティに変換します。</span><span class="sxs-lookup"><span data-stu-id="13d13-105">entitizes invalid XML characters when they are returned within FOR XML queries that do not use the TYPE directive.</span></span>  
  
 <span data-ttu-id="13d13-106">XML 1.0 準拠のパーサーは、これらの文字がエンティティであるかどうかにかかわらず解析エラーを返しますが、エンティティで表現すると XML 1.1 への準拠度が高くなります。</span><span class="sxs-lookup"><span data-stu-id="13d13-106">Although XML 1.0 conformant parsers raise parse errors regardless of whether these characters are entitized or not, the entitized form is better aligned with XML 1.1.</span></span> <span data-ttu-id="13d13-107">エンティティによる表現は、XML 標準の今後のバージョンでも推奨されると考えられます。</span><span class="sxs-lookup"><span data-stu-id="13d13-107">The entitized form is also potentially better aligned with future versions of the XML standard.</span></span> <span data-ttu-id="13d13-108">また、コード内で無効な文字を検出しやすくなるため、デバッグが容易になります。</span><span class="sxs-lookup"><span data-stu-id="13d13-108">Additionally, it makes debugging simpler, because the code point of the invalid character becomes visible.</span></span>  
  
 <span data-ttu-id="13d13-109">XML ツールを使用している場合は、データ ストリーム中で無効な文字が見つかった場合は、どのような場合でも XML パーサーは失敗するので、対処する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="13d13-109">For users of XML tools, no workaround is required, because the XML parser will fail either way at the point where the invalid characters occur in the data stream.</span></span> <span data-ttu-id="13d13-110">XML 以外のツールを使用している場合は、エンティティとして表現すべき文字を検索するようにプログラミング ロジックを変更する必要が生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="13d13-110">If you use non-XML tools, this change can require you to update your programming logic to search for these characters as entitized values.</span></span>  
  
 <span data-ttu-id="13d13-111">FOR XML クエリ内の以下の空白文字が情報のやり取りの間に失われないようにするため、異なるエンティティに変換されます。</span><span class="sxs-lookup"><span data-stu-id="13d13-111">The following white space characters are entitized differently in FOR XML queries to preserve their presence through round-tripping:</span></span>  
  
-   <span data-ttu-id="13d13-112">要素のコンテンツおよび属性内: **hex(0D)** (キャリッジ リターン)</span><span class="sxs-lookup"><span data-stu-id="13d13-112">In element content and attributes: **hex(0D)** (carriage return)</span></span>  
  
-   <span data-ttu-id="13d13-113">属性のコンテンツ内: **hex(09)** (タブ)、 **hex(0A)** (ライン フィード)</span><span class="sxs-lookup"><span data-stu-id="13d13-113">In attribute content: **hex(09)** (tab), **hex(0A)** (line feed)</span></span>  
  
 <span data-ttu-id="13d13-114">これらの文字は出力に保持され、パーサーはこれらの文字を正規化しません。</span><span class="sxs-lookup"><span data-stu-id="13d13-114">These characters are preserved in output, and a parser will not normalize them.</span></span>  
  
## <a name="escape-rules"></a><span data-ttu-id="13d13-115">エスケープの規則</span><span class="sxs-lookup"><span data-stu-id="13d13-115">Escape Rules</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="13d13-116">の名前にスペースなどの XML では無効になる文字が含まれている場合、この名前は、無効な文字がエスケープ数値エンティティ エンコードに変換された XML 名に変換されます。</span><span class="sxs-lookup"><span data-stu-id="13d13-116">names that contain characters that are invalid in XML names, such as spaces, are translated into XML names in a way in which the invalid characters are translated into escaped numeric entity encoding.</span></span>  
  
 <span data-ttu-id="13d13-117">英字以外で XML 名に使用できる文字は、コロン (:) と下線 (_) の 2 つだけです。</span><span class="sxs-lookup"><span data-stu-id="13d13-117">There are only two non-alphabetic characters that can occur within an XML name: the colon (:) and the underscore (_).</span></span> <span data-ttu-id="13d13-118">コロンは既に名前空間用に予約されているので、エスケープ文字としてはアンダースコアが使われます。</span><span class="sxs-lookup"><span data-stu-id="13d13-118">Because the colon is already reserved for namespaces, the underscore is chosen as the escape character.</span></span> <span data-ttu-id="13d13-119">エンコードに使用されるエスケープの規則は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="13d13-119">Following are the escape rules that are used for encoding:</span></span>  
  
-   <span data-ttu-id="13d13-120">有効な XML 名の文字ではない UCS-2 文字は、XML 1.0 の仕様に従って、_xHHHH\_としてエスケープされます。</span><span class="sxs-lookup"><span data-stu-id="13d13-120">Any UCS-2 character that is not a valid XML name character, according to the XML 1.0 specification, is escaped as _xHHHH\_.</span></span> <span data-ttu-id="13d13-121">この HHHH は、その文字の 4 桁の 16 進数 UCS-2 コードを最上位ビットから順に表しています。</span><span class="sxs-lookup"><span data-stu-id="13d13-121">The HHHH stands for the four-digit hexadecimal UCS-2 code for the character in the most significant bit-first order.</span></span> <span data-ttu-id="13d13-122">たとえば、テーブル名 **Order Details** は、Order_x0020_Details のようにエンコードされます。</span><span class="sxs-lookup"><span data-stu-id="13d13-122">For example, the table name **Order Details** is encoded as Order_x0020_Details.</span></span>  
  
-   <span data-ttu-id="13d13-123">UCS-2 領域に適合しない文字 (U+00010000 ～ U+0010FFFF の範囲の UCS-4 追加分) は、_xHHHHHHHH\_のようにエンコードされます。</span><span class="sxs-lookup"><span data-stu-id="13d13-123">Characters that do not fit into the UCS-2 realm (the UCS-4 additions of the range U+00010000 to U+0010FFFF) are encoded as _xHHHHHHHH\_.</span></span> <span data-ttu-id="13d13-124">SQL Server 2000 以前の下位互換性モードで実行されている場合、この HHHHHHHH は、その文字の 8 桁の 16 進数 UCS-4 エンコードを表します。</span><span class="sxs-lookup"><span data-stu-id="13d13-124">The HHHHHHHH stands for the eight-digit hexadecimal UCS-4 encoding of the character, if under SQL Server 2000 backward compatibility mode.</span></span> <span data-ttu-id="13d13-125">それ以外の場合は、ISO 標準に合わせ、文字は _xHHHHHH\_の形式でエンコードされます。</span><span class="sxs-lookup"><span data-stu-id="13d13-125">Otherwise, the characters are encoded as_xHHHHHH\_, in order to align with the ISO standard.</span></span>  
  
-   <span data-ttu-id="13d13-126">アンダースコア文字は、その後に文字 x が続いていない場合はエスケープする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="13d13-126">The underscore character does not have to be escaped unless it is followed by the character x.</span></span> <span data-ttu-id="13d13-127">たとえば、テーブル名 **Order_Details** はエンコードされません。</span><span class="sxs-lookup"><span data-stu-id="13d13-127">For example, the table name **Order_Details** is not encoded.</span></span>  
  
-   <span data-ttu-id="13d13-128">識別子内のコロン (:) 文字はエスケープされません。このため、FOR XML クエリで名前空間の要素と属性名を生成できます。</span><span class="sxs-lookup"><span data-stu-id="13d13-128">The colon in identifiers is not escaped As a result, the namespace element and attribute names can be generated by the FOR XML query.</span></span> <span data-ttu-id="13d13-129">たとえば、次のクエリでは名前にコロンが含まれる名前空間属性が生成されます。</span><span class="sxs-lookup"><span data-stu-id="13d13-129">For example, the following query generates a namespace attribute that has a colon in the name:</span></span>  
  
    ```  
    SELECT 'namespace-urn' as 'xmlns:namespace',   
     1 as 'namespace:a'   
    FOR XML RAW  
    ```  
  
     <span data-ttu-id="13d13-130">クエリの結果は以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="13d13-130">The query produces this result:</span></span>  
  
    ```  
    <row xmlns:namespace="namespace-urn" namespace:a="1"/>  
    ```  
  
     <span data-ttu-id="13d13-131">XML 名前空間を追加する場合は、WITH XMLNAMESPACES を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="13d13-131">Note that WITH XMLNAMESPACES is the recommended way to add XML namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13d13-132">参照</span><span class="sxs-lookup"><span data-stu-id="13d13-132">See Also</span></span>  
 [<span data-ttu-id="13d13-133">FOR XML &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="13d13-133">FOR XML &#40;SQL Server&#41;</span></span>](for-xml-sql-server.md)  
  
  
