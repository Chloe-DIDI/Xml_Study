/*=============================================
   XmlDomTest02.java
   - 콘솔 기반 자바 프로그램
   - XML DOM 활용 → 로컬(local) XML 읽어내기
     (VEHICLES.xml)
==============================================*/
package com.test;

import javax.xml.parsers.DocumentBuilder;
import javax.xml.parsers.DocumentBuilderFactory;

import org.w3c.dom.Document;
import org.w3c.dom.Element;
import org.w3c.dom.Node;
import org.w3c.dom.NodeList;

public class xmlDomTest02
{
   public static void main(String[] args)
   {
      // 1. XML 파일을 메모리에 로드 → XML DOM 형성
      // 2. 루트 엘리먼트 접근
      // 3. 특정 하위 엘리먼트 접근 → 위치, 이름 등을 기준으로 접근
      // 4. 텍스트 노드(속성 노드) 접근 → 데이터 획득
      // 5. 결과 출력
      
      try
      {
         DocumentBuilderFactory factory = DocumentBuilderFactory.newInstance();
         DocumentBuilder builder = factory.newDocumentBuilder();
         Document xmlObj = null;
         
         String url = "memberList.xml";
         xmlObj = builder.parse(url);
         
         Element root = xmlObj.getDocumentElement();
         
         NodeList memberInfoNodeList = root.getElementsByTagName("memberInfo");
         
         // 노드 갯수 확인 테스트
         // System.out.println(memberInfoNodeList.getLength());
         
         for (int i = 0; i < memberInfoNodeList.getLength(); i++)
         {
            Node memberInfoNode = memberInfoNodeList.item(i);
            // 『getElementsByTagName()』 메소드가 이름을 통해 대상을 획득했다면,
            // 『item()』 메소드는 위치(인덱스)를 통해 대상을 획득하게 된다.
            
            Element memberInfoElement = (Element)memberInfoNode;
            
            System.out.printf("%s %s%n", getText(memberInfoElement, "name")
                              , getText(memberInfoElement, "telephone"));
            
            /*
             춘식이 010-1111-1111
             어피치 010-2222-2222
             */
            
            // 커리큘럼 추가 ------------------------------------------------------------

            // memberInfoElement로 부터 curriculumn NodeList 얻어오기
            NodeList curriculumnNodeList = memberInfoElement.getElementsByTagName("curriculumn");
            
            if (curriculumnNodeList.getLength() > 0)
            {
               Node curriculumnNode = curriculumnNodeList.item(0);
               Element curriculumnElement = (Element)curriculumnNode;
               
               // 방법 1
               /*
               NodeList subNodeList = curriculumnElement.getElementsByTagName("sub");
               for (int j = 0; j < subNodeList.getLength(); j++)
               {
                  Node subNode = subNodeList.item(j);
                  Element subElement = (Element)subNode;
                  System.out.printf("[%s] ", subElement.getTextContent());
               }
               System.out.println();
               */
               
               
               // 방법 2
               /*
               ------------------------------------------------
               Node Type   Named Content
               ------------------------------------------------
               1         ELEMENT_NODE
               2         ATTRIBUTE_NODE
               3         TEXT_NODE
               4         CDATA_SECTION_NODE
               5         ENTITY_REFERENCE_NODE
               6         ENTITY_NODE
               7         PROCESSING_INSTRUCTION_NODE
               8         COMMENT_NODE
               9         DOCUMENT_NODE
               10         DOCUMENT_TYPE_NODE
               11         DOCUMENT_FRAGMENT_NODE
               12         NOTATION_NODE
               ------------------------------------------------
                */
               
               NodeList subNodeList = curriculumnElement.getChildNodes();      // 체크
               for (int j = 0; j < subNodeList.getLength(); j++)
               {
                  Node subNode = subNodeList.item(j);
                  if (subNode.getNodeType() == 1)      // subNode가 ELEMENT_NODE로 구성되어 있다면
                  {
                     Element subElement= (Element)subNode;
                     System.out.printf("[%s] ", subElement.getTextContent());
                  }
               }
               System.out.println();
            }
            
            // 커리큘럼 추가 ------------------------------------------------------------
            
         }
         
      } catch (Exception e)
      {
         System.out.println(e.toString());
      }
      
   }
   
   public static String getText(Element parent, String tagName)
   {
      String result = "";
      
      Node node = parent.getElementsByTagName(tagName).item(0);
      Element element = (Element)node;
      
      result = element.getChildNodes().item(0).getNodeValue();
      
      return result;
   }
}