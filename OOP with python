객체 지향 프로그래밍(영어: Object-Oriented Programming, OOP)
일반적으로 프로그램을 만들때 항상 염두에 둬야할 아주 중요한 포인트 2가지가 있습니다.
같은 코드를 반복하지 않는다.
코드는 항상 바뀔 수 있다는 것을 기억한다.
 이름, 에너지, 데미지, 인벤토리를 가진 간단한 케릭터를 만들어 보려고 합니다
 
hero_name = '아이언맨'
hero_health = 100
hero_damage = 200
hero_inventory = [
    {'gold': 500},
    {'weapon': '레이저'}
]
하나씩 추가하기
# 히어로 1
hero_1_name = '아이언맨'
hero_1_health = 100
hero_1_damage = 200
hero_1_inventory = [
    {'gold': 500},
    {'weapon': '레이저'}
]
# 히어로 2
hero_2_name = '데드풀'
hero_2_health = 300
hero_2_damage = 30
hero_2_inventory = [
    {'gold': 300},
    {'weapon': '장검'}
]
# 히어로 3
hero_3_name = '울버린'
hero_3_health = 200
hero_3_damage = 50
hero_3_inventory = [
    {'gold': 350},
    {'weapon': '클로'}
]
# 몬스터 1
monster_1_name = '고블린'
monster_1_health = 90
monster_1_damage = 30
monster_1_inventory = [
    {'gold': 50},
    {'weapon': '창'}
]
# 몬스터 2
monster_2_name = '드래곤'
monster_2_health = 200
monster_2_damage = 80
monster_2_inventory = [
    {'gold': 200},
    {'weapon': '화염'}
]
# 몬스터 3
monster_3_name = '뱀파이어'
monster_3_health = 80
monster_3_damage = 120
monster_3_inventory = [
    {'gold': 1000},
    {'weapon': '최면술'}
]
리스트를 이용하여 코드를 바꿔봅니다.
hero_name = ['아이언맨', '데드풀', '울버린']
hero_health = [100, 300, 200]
hero_damage = [200, 30, 50]
hero_inventory = [
    {'gold': 500,'weapon': '레이저'},
    {'gold': 300, 'weapon': '장검'},
    {'gold': 350, 'weapon': '클로'}
]
monster_name = ['고블린', '드래곤', '뱀파이어']
monster_health = [90, 200, 80]
monster_damage = [30, 80, 120]
monster_inventory = [
    {'gold': 50,'weapon': '창'},
    {'gold': 200, 'weapon': '화염'},
    {'gold': 1000, 'weapon': '최면술'}
]
오류가 날 가능성들을 살펴보게 된다면
import json
hero_name = ['아이언맨', '데드풀', '울버린']
hero_health = [100, 300, 200]
hero_damage = [200, 30, 50]
hero_inventory = [
    {'gold': 500,'weapon': '레이저'},
    {'gold': 300, 'weapon': '장검'},
    {'gold': 350, 'weapon': '클로'}
]
monster_name = ['고블린', '드래곤', '뱀파이어']
monster_health = [90, 200, 80]
monster_damage = [30, 80, 120]
monster_inventory = [
    {'gold': 50,'weapon': '창'},
    {'gold': 200, 'weapon': '화염'},
    {'gold': 1000, 'weapon': '최면술'}
]
# 히어로가 죽으면 호출되는 함수
def hero_dies(hero_index):
    del hero_name[hero_index]
    del hero_health[hero_index]
    del hero_damage[hero_index]
    # <--- 실수로 del hero_inventory[hero_index]하지 않았다면
    
hero_dies(0)
print hero_name[0]
print hero_health[0]
print hero_damage[0]
print json.dumps(hero_inventory[0], ensure_ascii=False)
저장후 실행시
----------------------------------
데드풀
300
30
{"weapon": "레이저", "gold": 500}
위의 코드와 같이 히어로의 에너지가 0이 되어 죽었을때 히어로를 리스트에서 지우는 함수를 추가했습니다. 그런데 개발자가 실수로 코드 한줄을 넣지 않았다면 "데드풀"이 죽은 "아이언맨"의 레이저를 사용하게 되는 문제가 발생합니다.
이러한 문제는 밑의 코드와 같이 각 히어로의 데이터를 파이썬 사전에 넣어 리스트로 묶어서 해결할 수 있습니다.
import json
heroes = [
    {'name': '아이언맨', 'health': 100, 'damage': 200, 'inventory': {'gold': 500, 'weapon': '레이저'}},
    {'name': '데드풀', 'health': 300, 'damage': 30, 'inventory': {'gold': 300, 'weapon': '장검'}},
    {'name': '울버린', 'health': 200, 'damage': 50, 'inventory': {'gold': 350, 'weapon': '클로'}}
]
monsters = [
    {'name': '고블린', 'health': 90, 'damage': 30, 'inventory': {'gold': 50, 'weapon': '창'}},
    {'name': '드래곤', 'health': 200, 'damage': 80, 'inventory': {'gold': 200, 'weapon': '화염'}},
    {'name': '뱀파이어', 'health': 80, 'damage': 120, 'inventory': {'gold': 1000, 'weapon': '최면술'}}
]
print json.dumps(heroes, ensure_ascii=False)
del heroes[0]
print json.dumps(heroes, ensure_ascii=False)
[{"inventory": {"weapon": "레이저", "gold": 500}, "health": 100, "name": "아이언맨", "damage": 200},
{"inventory": {"weapon": "장검", "gold": 300}, "health": 300, "name": "데드풀", "damage": 30},
{"inventory": {"weapon": "클로", "gold": 350}, "health": 200, "name": "울버린", "damage": 50}]
[{"inventory": {"weapon": "장검", "gold": 300}, "health": 300, "name": "데드풀", "damage": 30},
{"inventory": {"weapon": "클로", "gold": 350}, "health": 200, "name": "울버린", "damage": 50}]
만약 히어로의 인벤토리에 여러가지 아이템을 가진 가방이 있다고 했을 때 사전과 리스트는 중첩이 되고 코드는 더욱 더 복잡해질 것 입니다.
 OOP를 사용할 때 입니다. 
 
 위에서 클래스는 새로운 데이터 타입을 만드는 블루프린트라고 했습니다. 블루프린트란 한국말로 "청사진"이라고 부르며 건축물이나 자동차를 설계한 도면입니다. 자동차의 모델을 디자인하고 설계한 블루프린트를 이용하여 같은 모델의 자동차를 원하는 만큼 찍어 낼 수 있는거죠. 프로그래밍의 클래스도 같은 개념입니다.
 위의 히어로와 몬스터 또한 같은 종류의 데이터를 가지고 있기 때문에 다음의 코드와 같이 클래스를 이용하여 논리적인 집합으로 묶을 수가 있습니다
 
 class Character(object):
    def __init__(self, name, health, damage, inventory):
        self.name = name
        self.health = health
        self.damage = damage
        self.inventory = inventory
        
    def __repr__(self):
        return self.name
        
# Character 클래스의 오브젝트 생성
heroes = []
heroes.append(Character('아이언맨', 100, 200, {'gold': 500, 'weapon': '레이저'}))
heroes.append(Character('데드풀', 300, 30, {'gold': 300, 'weapon': '장검'}))
heroes.append(Character('울버린', 200, 50, {'gold': 350, 'weapon': '클로'}))
monsters = []
monsters.append(Character('고블린', 90, 30, {'gold': 50, 'weapon': '창'}))
monsters.append(Character('드래곤', 200, 80, {'gold': 200, 'weapon': '화염'}))
monsters.append(Character('뱀파이어', 80, 120, {'gold': 1000, 'weapon': '최면술'}))
print heroes  # 히어로 리스트 확인
print monsters  # 몬스터 리스트 확인
del heroes[0]  # 히어로 리스트에서 아이언맨 삭제
print heroes  # 히어로 리스트 재확인
------------------------------------
[아이언맨, 데드풀, 울버린]
[고블린, 드래곤, 뱀파이어]
[데드풀, 울버린]
"Character"라는 클래스를 사용하여 OOP를 구현해 보았습니다
위 자료는 
http://schoolofweb.net/blog/posts/%ED%8C%8C%EC%9D%B4%EC%8D%AC-oop-part-1-%EA%B0%9D%EC%B2%B4-%EC%A7%80%ED%96%A5-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8Doop%EC%9D%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80-%EC%99%9C-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94%EA%B0%80/
의 자료입니다 끝나고 수정할게요 
