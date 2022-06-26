package coverage

import (
	"os"
	"reflect"
	"testing"
	"time"
)

// DO NOT EDIT THIS FUNCTION
func init() {
	content, err := os.ReadFile("students_test.go")
	if err != nil {
		panic(err)
	}
	err = os.WriteFile("autocode/students_test", content, 0644)
	if err != nil {
		panic(err)
	}
}

// WRITE YOUR CODE BELOW
func TestPeople_Len(t *testing.T) {
	var people People
	if !checkLength(people, 0) {
		t.Errorf("People length should be 0, but it not")
	}

	length := 3
	for i := 0; i < length; i++ {
		people = append(people, Person{})
	}

	if !checkLength(people, length) {
		t.Errorf("People length should be %d, but it not", length)
	}

}

func checkLength(p People, length int) bool {
	if p.Len() != length {
		return false
	}
	return true
}

func TestPeople_Less(t *testing.T) {
	var people People
	now := time.Time{}

	people = append(people, Person{"Base", "Zero", now})
	people = append(people, Person{"Plus", "1Day", now.Add(24 * time.Hour)})
	people = append(people, Person{"Minus", "2Days", now.Add(-48 * time.Hour)})

	if people.Less(0, 1) {
		t.Errorf("Return true, but must return false")
	}

	if !people.Less(0, 2) {
		t.Errorf("Return false, but must return true")
	}

	if !people.Less(1, 2) {
		t.Errorf("Return false, but must return true")
	}
}

func TestPeople_Swap(t *testing.T) {
	var people People
	now := time.Time{}

	person1 := Person{"First", "Man", now}
	person2 := Person{"Second", "Man", now.Add(24 * time.Hour)}

	people = append(people, person1)
	people = append(people, person2)

	people.Swap(0, 1)

	if people[0] != person2 || people[1] != person1 {
		t.Errorf("People Swap is wrong")
	}
}
func TestGoodMatrix_New(t *testing.T) {
	matrix, err := New("1 1 1 \n 2 2 2")

	if err != nil {
		t.Errorf("Something wrong")
	}

	if matrix.rows != 2 {
		t.Errorf("Something wrong with rows, not expected count ")
	}
	if matrix.cols != 3 {
		t.Errorf("Something wrong with cols, not expected count ")
	}

	var curr [6]int
	copy(curr[:], matrix.data[0:])

	res := [6]int{1, 1, 1, 2, 2, 2}
	if curr != res {
		t.Errorf("Something wrong with data, not expected array ")
	}
}

func TestBadMatrix_New(t *testing.T) {
	_, err := New("1 1 1 \n 2 2 ")

	if err == nil {
		t.Errorf("Something wrong, expexted error")
	}

	_, err2 := New("a 1 1 \n a 2 ")

	if err2 == nil {
		t.Errorf("Something wrong, expexted error")
	}
}

func TestMatrix_Rows(t *testing.T) {
	matrix, _ := New("1 1 1 \n 2 2 2")

	res := [][]int{{1, 1, 1}, {2, 2, 2}}

	if !reflect.DeepEqual(matrix.Rows(), res) {
		t.Errorf("Something wrong with matrix.Rows(), not expected slice ")
	}
}

func TestMatrix_Cols(t *testing.T) {
	matrix, _ := New("1 1 1 \n 2 2 2")

	res := [][]int{{1, 2}, {1, 2}, {1, 2}}

	if !reflect.DeepEqual(matrix.Cols(), res) {
		t.Errorf("Something wrong with matrix.Cols(), not expected slice ")
	}
}

func TestMatrix_Set(t *testing.T) {
	matrix, _ := New("1 1 1 \n 2 2 2")

	if matrix.Set(-1, 0, 5) {
		t.Errorf("Something wrong, matrix.Set(-1, 0, 5) return true")
	}

	if matrix.Set(0, -1, 5) {
		t.Errorf("Something wrong, matrix.Set(0, -1, 5) return true")
	}

	if matrix.Set(5, 0, 5) {
		t.Errorf("Something wrong, matrix.Set(5, -1, 5) return true (but have only 2 rows)")
	}

	if matrix.Set(0, 5, 5) {
		t.Errorf("Something wrong, matrix.Set(0, 5, 5) return true (but have only 3 cols)")
	}

	if !matrix.Set(0, 0, 5) {
		t.Errorf("Something wrong,return false on correct data")
	}

	if matrix.data[0] != 5 {
		t.Errorf("Something wrong, not expected value")
	}
}
