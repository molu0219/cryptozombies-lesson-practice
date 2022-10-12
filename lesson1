pragma solidity ^0.4.25;  // solidity version


contract ZombieFactory {
    
    // a way for contract to communicate with front-end app when something changed
    event NewZombie(uint zombieId, string name, uint dna);
    
    // unsign interger 0~255, parameters will store on block
    uint dnaDigits = 16;
    uint dnaModulus = 10 ** dnaDigits;
    
    // structs
    struct Zombie {
        string name;
        uint dna;
    }

    // structure array
    Zombie[] public zombies;

    // private function with "_"
    function _createZombie(string _name, uint _dna) private {
        uint id = zombies.push(Zombie(_name, _dna)) - 1;
        emit NewZombie(id, _name, _dna);
    }
    
    // view: only viewing the data, not modifying it.
    function _generateRandomDna(string _str) private view returns (uint) {
        uint rand = uint(keccak256(abi.encodePacked(_str)));
        return rand % dnaModulus;
    }
    
    
    function createRandomZombie(string _name) public {
        uint randDna = _generateRandomDna(_name);
        _createZombie(_name, randDna);
    }

}
