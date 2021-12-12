# 5Z1

## 3E.

a. Konfiguracja puli adresowej dla podsieci na moście bridge2: ```iptables -I DOCKER-USER -m iprange -i bridge2 ! --src-range (from_address)-(to_address) -j DROP```

b. Kontenery D2 i S1 nie mogą wykorzystać mechanizmu dynamicznego przypisywania adresów (DHCP) jeśli w tym segmencie sieci dostępny byłby serwer DHCP. Wymaga to utworzenia docker network na macvlan albo ipvlan driver, a następnie skorzystania z DHCP IPAM driver.

# 5Z3

## 1.

Nie można używać aliasów do komunikacji pomiędzy kontenerami przyłączonymi do dwóch różnych sieci, ale pracujących w trybie mostu definiowanego przez użytkownika.
Zarówno ```--network-alias``` jak i ```--alias``` nadają alias o zasięgu tylko obecnej sieci.

## 2E.
W przypadku pomyślnej konfiguracji w zadaniu 5Z1 sieci wykorzystującej most bridge2 niemożliwe jest korzystanie ze zdefiniowanych aliasów na hoście macierzystym przy połączeniach do kontenera S1 lub D2, ponieważ aliasy nie mają żadnego wpływu na hosta macierzystego, obowiązują one tylko w wyznaczonej sieci w trybie bridge i dostępne są tylko z kontenerów.