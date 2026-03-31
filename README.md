# Discrete-Math-Practicals
# ================================


from itertools import permutations

# -------------------------------
# 1. SET CLASS
# -------------------------------

    class SET:
        def __init__(self, elements=None):
            self.s = set(elements) if elements else set()
            
        def is_member(self, x):
            return x in self.s
    
        def union(self, other):
            return self.s | other.s
    
        def intersection(self, other):
            return self.s & other.s
    
        def difference(self, other):
            return self.s - other.s


# -------------------------------
# 2. RELATION CLASS
# -------------------------------
    class Relation:
        def __init__(self, matrix):
            self.a = matrix
            self.n = len(matrix)
    
        def is_reflexive(self):
            return all(self.a[i][i] == 1 for i in range(self.n))
    
        def is_symmetric(self):
            return all(self.a[i][j] == self.a[j][i]
                       for i in range(self.n)
                       for j in range(self.n))
    
        def is_transitive(self):
            for i in range(self.n):
                for j in range(self.n):
                    for k in range(self.n):
                        if self.a[i][j] and self.a[j][k] and not self.a[i][k]:
                            return False
            return True


# -------------------------------
# 3. PERMUTATIONS
# -------------------------------
    def generate_permutations(s):
        return ["".join(p) for p in permutations(s)]


# -------------------------------
# 4. EQUATION SOLUTIONS
# -------------------------------
    def equation_solutions(C):
        result = []
        for x1 in range(C+1):
            for x2 in range(C+1):
                for x3 in range(C+1):
                    if x1 + x2 + x3 == C:
                        result.append((x1, x2, x3))
        return result


# -------------------------------
# 5. POLYNOMIAL
# -------------------------------
    def polynomial(n):
        return 4*n*n + 2*n + 9


# -------------------------------
# 6. COMPLETE GRAPH (MATRIX)
# -------------------------------
    def is_complete_matrix(g):
        n = len(g)
        for i in range(n):
            for j in range(n):
                if i != j and g[i][j] == 0:
                    return False
        return True


# -------------------------------
# 7. COMPLETE GRAPH (LIST)
# -------------------------------
    def is_complete_list(adj):
        n = len(adj)
        return all(len(adj[i]) == n-1 for i in range(n))


# -------------------------------
# 8. IN-DEGREE & OUT-DEGREE
# -------------------------------
    def degree(g):
        n = len(g)
        deg = []
        for i in range(n):
            out_d = sum(g[i])
            in_d = sum(g[j][i] for j in range(n))
            deg.append((i, in_d, out_d))
        return deg
