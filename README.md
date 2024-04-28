# PoS 전환

### description
> 이곳은 팝캣티움 PoS 전환에 필요한 내용을 정리하는 곳입니다.

### 준비물
- [geth](https://github.com/ethereum/go-ethereum/releases/tag/v1.11.6) (v1.11.6):  팝캣티움에 맞게 genesis 및 포크 관련 내용 수정 필요
- [deposit contract](https://github.com/ethereum/consensus-specs/blob/master/solidity_deposit_contract/deposit_contract.sol):  비콘체인에 코인 예치
- [key generator](https://github.com/ethereum/staking-deposit-cli):  코인 예치와 관련된 도구
- consensus client:  Prysm, Lighthouse 중에 사용하기 편한걸로 선택
- beacon explorer: beaconcha.in, ethstakers중 사용하기 편한걸로 선택

### 개념 정리
- pos: https://ethereum.org/developers/docs/consensus-mechanisms/pos
- pos key: https://ethereum.org/developers/docs/consensus-mechanisms/pos/keys
- paris upgrade: https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/paris.md
- EIP-3675: https://eips.ethereum.org/EIPS/eip-3675
-  beacon(디사이퍼): https://medium.com/decipher-media/이더리움-비콘-체인-이해하기-c0d6a80f3ecf
- pos 인프라 설명: https://medium.com/a41-ventures/이제는-알아야-하는-pos-ethereum-인프라-이야기-dc9f761a593c
- enr: https://ethereum.org/ko/developers/docs/networking-layer/network-addresses/
- deposit-processing: https://eth2book.info/capella/part2/deposits-withdrawals/deposit-processing/
### 도구 정리
- lighthouse: https://lighthouse-book.sigmaprime.io/
- prysm: https://docs.prylabs.network/docs/getting-started
- beacon explorer: https://github.com/gobitfly/eth2-beaconchain-explorer
- ethstakers: https://github.com/ethstakersclub/ethstakersclub
- beaconcha.in docs: https://kb.beaconcha.in/
### 참고 문서
- 제네시스 pos 병합: https://dev.to/q9/how-to-merge-an-ethereum-network-right-from-the-genesis-block-3454
- testnet pos실행: https://medium.com/onther-tech/eth-2-0-testnet-introduction-d92e02d265de
- 라이트하우스 관련 에러: https://github.com/sigp/lighthouse/issues/4552
- 라이트하우스 테스트넷 config: https://github.com/eth-clients/eth2-networks/blob/master/lighthouse/testnet5/config.yaml
- deposit contract 사용: https://velog.io/@vamprodo47/deposit-contract-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0
- deposit-cli 설명: https://help.joinstakehouse.com/en/articles/6206942-how-do-i-stake-a-validator-using-the-ethereum-cli-mainnet-testnet
- 로컬 이더리움 테스트넷: https://github.com/ethereum/local-testnet
- 로컬 이더리움 테스트넷2 : https://gist.github.com/ryanorendorff/2d3745a66e0d62eca8ea2506ccbc9882
- 테스트넷  Genesis 생성도구: https://github.com/protolambda/eth2-testnet-genesis
- 테스트넷 만드는 방법: https://notes.ethereum.org/@parithosh/H1MSKgm3F
- Lighthouse 테스트넷 생성: https://github.com/sigp/lighthouse/tree/stable/scripts/local_testnet
- engine api: https://hackmd.io/@danielrachi/engine_api

### 팝캣티움 머지 작업순서
1. geth를 팝캣티움에 맞게 수정
2. pos 전환 하드포크 내용 추가
3. 팝캣티움에 deposit 컨트랙트 배포
4. staking에 참여할 키 생성, 입금 진행
5. bconsensus 클라이언트에 deposit 컨트랙트, 체인id 등 필요 변수값 넣어서 실행
6. genesis.ssz 생성
7. 실행노드와 합의노드 연결 확인
8. 설정해둔 시간에 pos 전환 되는지 확인
9. 각 클라이언트 정상 작동 하는지 확인
10. 비콘 체인 익스플로러 연동

### PoS 전환 작업 순서
#### PoW => PoS 머지시
 - pow or poa 실행 가능한 geth 버전 준비
 - genesis.json 세팅
 - lighthoise 세팅 (다른 컨세서스 노드 사용 가능)
 - genesis.json에 세팅한 시간에 merge 되는지 확인
 - 블록 생성 확인
#### PoS 네트워크 실행
-  Lighthouse 테스트넷 생성 문서 참고