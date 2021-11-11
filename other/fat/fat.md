# FAT이란?

FAT(File Allocation Table)인데 직역하자면 파일 활당 테이블이다. 이는 이름 그대로 파일의 할당 정보를 표현한 테이블이라고 할 수 있다.

FAT파일 시스템은 MS-DOS때부터 사용되었는데 Windows에서부터는 파일시스템 자체를 가리키는 용어가 되었다.

우선 추상적인 FAT32 파일 시스템의 구조는 아래와 같다.

|               |          |           |     |
| ------------- | -------- | --------- | --- |
| Reserved Area | FAT Area | Data Area |

크게 예약영역(Reserved Area)과 FAT Area, DATA Area로 나누어진다.

좀 더 자세히 나눈다면

|     |               |       |       |                |           |             |
| --- | ------------- | ----- | ----- | -------------- | --------- | ----------- |
| BR  | Reserved Area | FAT#1 | FAT#2 | Root Directory | Data Area | Unused Area |

이렇게 되는데 여기서

1. BR은 Boot Record로써 파일시스템의 첫번째 섹터를 의미한다. 대개 Reserved Area에 포함되기에 Reserved Area의 첫번째 섹터라고도 한다. 대개 섹터 1개를 가지며(512 byte) 윈도우를 부팅하기 위한 코드와 FAT 파일 시스템의 여러 설정 값이 저장된다.

2. Reserved Area는 이름 그대로 예약된 영역으로 FAT32기준으로 32섹터를 할당한다. Reserved Area를 좀더 보면

   |     |        |            |                 |                    |               |            |                 |     |
   | --- | ------ | ---------- | --------------- | ------------------ | ------------- | ---------- | --------------- | --- |
   | BR  | FSINFO | Boot Strap | Reserved Sector | Boot Record Backup | FSINFO Backup | Boot Strap | Reserved Sector |

   위와 같이 되는데 순서대로 보자면

   BR은 1.에서 설명한 Boot Record이며

   FSINFO는 (File System Information)이며 파일 시스템의 정보를 저장한다.

   Boot Record Backup은 BR의 정보를 백업하는 섹터이다.

   Book Strap은 부팅시 동작해야 할 명령 코드가 들어있는 섹터이다.

3. FAT#1과 FAT#2가 있는데 FAT#2는 FAT#1의 백업 영역이다. FAT#1은 파일이나 디렉터리의 할당 유무가 기록되며 클러스터 단위로 기록되며 1개의 클러스터에 대한 사용 유무를 기록하기 위해 4 byte 공간이 필요하다.

4. Data Area는 실제 파티션 안에 만들어지는 데이터인 파일이나 디렉터리가 저장되어 있는 영역이며 이 영역의 시작은 Root Directory가 할당 받으며 해당 영역에 대해서는 Directory Entry의 형식으로 기록한다.

# 참고자료

> http://forensic-proof.com/archives/370

> https://gedor.tistory.com/5

> https://imsosimin.com/47
