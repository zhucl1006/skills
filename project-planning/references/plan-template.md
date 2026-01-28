# [Feature Name] Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use project-workflow to implement this plan task-by-task.

**Goal:** [一句话描述要构建什么]

**Architecture:** [2-3 句话描述实现方法]

**Tech Stack:** [关键技术/库]

---

## Prerequisites

- [ ] Design document approved
- [ ] Dependencies installed
- [ ] Development environment set up
- [ ] Tests framework configured

---

## Task 1: [Component Name]

**Files:**
- Create: `exact/path/to/file.py`
- Modify: `exact/path/to/existing.py:123-145`
- Test: `tests/exact/path/to/test.py`

### Step 1: Write the failing test

```python
def test_specific_behavior():
    """Test that [specific behavior] works correctly."""
    # Arrange
    input_data = "test input"

    # Act
    result = function(input_data)

    # Assert
    assert result == "expected output"
```

### Step 2: Run test to verify it fails

**Run:**
```bash
pytest tests/path/test.py::test_specific_behavior -v
```

**Expected output:**
```
FAILED tests/path/test.py::test_specific_behavior
NameError: name 'function' is not defined
```

### Step 3: Write minimal implementation

```python
def function(input_data):
    """[Function description]."""
    # Minimal implementation to make test pass
    return "expected output"
```

### Step 4: Run test to verify it passes

**Run:**
```bash
pytest tests/path/test.py::test_specific_behavior -v
```

**Expected output:**
```
PASSED tests/path/test.py::test_specific_behavior
```

### Step 5: Commit

```bash
git add tests/path/test.py src/path/file.py
git commit -m "feat: add [specific feature]"
```

---

## Task 2: [Component Name]

[同上结构]

---

## Task 3: [Component Name]

[同上结构]

---

## Integration Testing

### Test 1: [Integration scenario]

**Files:**
- Test: `tests/integration/test_integration.py`

**Test code:**
```python
def test_integration_scenario():
    """Test that components work together correctly."""
    # Test implementation
    pass
```

**Run:**
```bash
pytest tests/integration/test_integration.py -v
```

---

## Documentation Updates

### Update 1: [Document name]

**File:** `docs/path/to/document.md`

**Changes:**
- Add section about [new feature]
- Update API documentation
- Add usage examples

### Update 2: [Document name]

[同上]

---

## Final Verification

### Checklist

- [ ] All tests pass
- [ ] Code follows project conventions (check AGENTS.md)
- [ ] Documentation updated
- [ ] No security vulnerabilities
- [ ] Performance acceptable
- [ ] Error handling complete

### Run full test suite

```bash
pytest tests/ -v
```

### Run linter

```bash
# Example for Python
flake8 src/
pylint src/

# Example for JavaScript
eslint src/
```

---

## Execution Record

| Date | Task | Status | Notes |
|------|------|--------|-------|
| YYYY-MM-DD | Task 1 | ✓ Completed | [Notes] |
| YYYY-MM-DD | Task 2 | ✓ Completed | [Notes] |
| YYYY-MM-DD | Task 3 | ⏳ In Progress | [Notes] |

---

## Notes

### Technical Decisions

- Decision 1: [Rationale]
- Decision 2: [Rationale]

### Issues Encountered

- Issue 1: [Description and resolution]
- Issue 2: [Description and resolution]

### Future Improvements

- Improvement 1: [Description]
- Improvement 2: [Description]
