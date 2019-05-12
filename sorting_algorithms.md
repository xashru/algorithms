```
// ---------------bubble sort--------------
vector<int> bubble_sort(vector<int> v) {
	size_t n = v.size();
	for (size_t i = 0; i < n; i++) {
		bool swapped = false;
		for (size_t j = 1; j < n; j++) {
			if (v[j-1] > v[j]) {
				swap(v[j - 1], v[j]);
				swapped = true;
			}
		}
		if (!swapped) break;
	}
	return v;
}

// --------------selection sort-----------------
vector<int> selection_sort(vector<int> v) {
	size_t n = v.size();
	for (size_t i = 0; i < n; ++i) {
		int min_index = i;
		for (int j = i + 1; j < n; j++) {
			if (v[j] < v[min_index]) {
				min_index = j;
			}
		}
		swap(v[i], v[min_index]);
	}
	return v;
}


//--------------------insertion sort--------------
// insertion sort is suitable for datasets that are 
vector<int> insertion_sort(vector<int> v) {
	for (int i = 1; i < v.size(); i++) {
		int j = i;
		while (j > 0 && v[j-1] > v[j]) {
			swap(v[j], v[j - 1]);
			j--;
		}
	}
	return v;
}


// ------------------merge sort-----------------
//merge routine
void merge(vector<int>& v, vector<int>& helper, int low, int mid, int high) {
	for (int i = low; i <= high; i++) {
		helper[i] = v[i];
	}
	int left = low;
	int right = mid + 1;
	int current = low;
	while (left <= mid && right <= high) {
		if (helper[left] <= helper[right]) {
			v[current] = helper[left];
			left++;
		}
		else {
			v[current] = helper[right];
			right++;
		}
		current++;
	}
	while (left <= mid) {
		v[current++] = helper[left++];
	}
}

// merge sort helper
void merge_sort(vector<int>& v, vector<int>& helper, int low, int high) {
	if (low < high) {
		int mid = low + (high - low) / 2;
		merge_sort(v, helper, low, mid);
		merge_sort(v, helper, mid + 1, high);
		merge(v, helper, low, mid, high);
	}
}

// merge sort
vector<int> merge_sort(vector<int> v) {
	vector<int> helper(v.size());
	merge_sort(v, helper, 0, v.size() - 1);
	return v;
}

// ---------------------quick sort-------------------

// partition routine
int partition(vector<int>& v, int left, int right) {
	int pivot = v[left + (right-left)/2];
	while (left <= right) {
		while (v[left] < pivot) left++;
		while (v[right] > pivot) right--;
		if (left <= right) {
			swap(v[left], v[right]);
			left++;
			right--;
		}
	}
	return left;
}


void quick_sort(vector<int>& v, int left, int right) {
	int index = partition(v, left, right);
	if (left < index-1) {
		quick_sort(v, left, index-1);
	}
	if (right > index) {
		quick_sort(v, index, right);
	}
}

vector<int> quick_sort(vector<int> v) {
	quick_sort(v, 0, v.size() - 1);
	return v;
}
