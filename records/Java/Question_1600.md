# [LeetCode Records](../../README.md) - Question 1600 Throne Inheritance

### Attempt 1: Use a HashMap to store the parent and its children key-value pairs and a HashSet to store the dead members
```java
class ThroneInheritance {

    private String kingName;
    private Map<String, List<String>> familyMemberMap;
    private Set<String> deadFamilyMemberSet;

    public ThroneInheritance(String kingName) {
        this.kingName = kingName;
        this.familyMemberMap = new HashMap<>();
        familyMemberMap.put(kingName, new ArrayList<>());
        this.deadFamilyMemberSet = new HashSet<>();
    }
    
    public void birth(String parentName, String childName) {
        familyMemberMap.get(parentName).add(childName);
        familyMemberMap.put(childName, new ArrayList<>());
    }
    
    public void death(String name) {
        deadFamilyMemberSet.add(name);
    }
    
    public List<String> getInheritanceOrder() {
        List<String> ans = new ArrayList<>();

        getInheritanceOrderRecursion(ans, kingName);

        return ans;
    }

    private void getInheritanceOrderRecursion(List<String> ans, String parentName) {
        if (!deadFamilyMemberSet.contains(parentName)) {
            ans.add(parentName);
        }
        
        for (String childName : familyMemberMap.get(parentName)) {
            getInheritanceOrderRecursion(ans, childName);
        }
    }
}

/**
 * Your ThroneInheritance object will be instantiated and called as such:
 * ThroneInheritance obj = new ThroneInheritance(kingName);
 * obj.birth(parentName,childName);
 * obj.death(name);
 * List<String> param_3 = obj.getInheritanceOrder();
 */
```
- Runtime: 261 ms (Beats: 68.00%)
- Memory: 105.30 MB (Beats: 28.80%)

<br>
